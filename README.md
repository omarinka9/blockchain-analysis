# blockchain-analysis
Creating a utility for blockchain analysis
import requests
from datetime import datetime

def get_blockchain_info():
    url = 'https://blockchain.info/latestblock'
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        return {
            'hash': data['hash'],
            'height': data['height'],
            'time': datetime.utcfromtimestamp(data['time']).strftime('%Y-%m-%d %H:%M:%S')
        }
    else:
        print(f'Ошибка при получении данных: {response.status_code}')
        return None

if __name__ == '__main__':
    info = get_blockchain_info()
    if info:
        print(f'Хэш последнего блока: {info["hash"]}')
        print(f'Высота блока: {info["height"]}')
        print(f'Время создания блока: {info["time"]}')
