製品の在庫管理API
====

製品の在庫管理の FastAPI を作成した。製品名（product_name）、製品価格（price）といった情報を登録（create）・参照（read）・更新（update）・削除（delete）できた 。操作に不備があった場合、エラーコードを表示した。
さらに、このFastAPIをAWSにデプロイした。

## Demo

![image](https://github.com/kutsumasanari/portofolio/6製品在庫管理 API/MyVideo_1.gif)

## 使い方

```
uvicorn content.main:app --reload
```


| 動作 | エラー内容とエラーコード | 例 |
| --- | --- | --- |
| create (登録) | 受け取った JSON の項目が、product_name, price が揃っていなかった場合、{“error_code”: “1”}を返す | POST {“product_name”: “iPhone”} → {“error_code”: “1”} |
| create (登録) update (更新) | price の値が数字ではなかった場合、{“error_code”: “2”}を返す | {“product_name”: “iPhone”, “price”: “test”} → {“error_code”: “2”} |
| create (登録) update (更新) | price の値がマイナスだった場合、{“error_code”: “3”}を返す | {“product_name”: “iPhone”, “price”: -1000} → {“error_code”: “3”} |
| delete (削除) | JSON の product_name のデータがデータベースに無い場合、{“error_code”: “4”}を返す | Example: {“test”: “test”} → {“error_code”: “4”} |