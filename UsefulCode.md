# Полезный код

### Отправка через бота telegram графика matplotlib

```python
import requests
import io

token = "токен_бота"
chat_id = "chat_id" # chat_id человека, которому нужно отправить график

buf = io.BytesIO()
plt.savefig(buf, format='png', transparent=True)
buf.seek(0)

url = f"https://api.telegram.org/bot{token}/sendPhoto?chat_id={chat_id}"

response = requests.post(url, files={"photo": buf})
buf.close()

# Вывод ответа
print(response.json())
```
