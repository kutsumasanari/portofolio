製品の在庫管理API
====

製品の在庫管理の FastAPI を作成した。製品名、製品価格といった情報を登録・参照・更新・削除できた 。操作に不備があった場合、エラーコードを表示した。このFastAPIをAWSにデプロイした。

## Demo

## 使い方

```
uvicorn content.main:app --reload
```

・受け取った JSON の項目が、product_name, price が揃っていなかった場合、{“error_code”: “1”}を返す

Example) POST {“product_name”: “iPhone”} → {“error_code”: “1”}

・price の値が数字ではなかった場合、{“error_code”: “2”}を返す

 Example) {“product_name”: “iPhone”, “price”: “test”} → {“error_code”: “2”}
 
・price の値がマイナスだった場合、{“error_code”: “3”}を返す

 Example) {“product_name”: “iPhone”, “price”: -1000} → {“error_code”: “3”}
