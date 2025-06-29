В Go маршалинг и анмаршалинг структур в JSON делается с помощью пакета `encoding/json`.

---

## 📦 Импорт:

```go
import "encoding/json"
```

---

## ✅ Маршалинг (Go → JSON)

```go
type User struct {
	ID    int    `json:"id"`
	Name  string `json:"name"`
	Email string `json:"email"`
}

u := User{
	ID:    1,
	Name:  "Alice",
	Email: "alice@example.com",
}

data, err := json.Marshal(u)
if err != nil {
	log.Fatal(err)
}

fmt.Println(string(data)) // {"id":1,"name":"Alice","email":"alice@example.com"}
```

---

## ✅ Анмаршалинг (JSON → Go)

```go
jsonStr := `{"id":1,"name":"Alice","email":"alice@example.com"}`
var u User

err := json.Unmarshal([]byte(jsonStr), &u)
if err != nil {
	log.Fatal(err)
}

fmt.Printf("%+v\n", u) // {ID:1 Name:Alice Email:alice@example.com}
```

---

## 📝 Примечания:

- Теги `json:"field_name"` задают, как поле будет выглядеть в JSON.
    
- Если тег `omitempty`, поле не попадёт в JSON, если оно пустое:
    
    ```go
    Email string `json:"email,omitempty"`
    ```
    

---

Хочешь — покажу, как маршалить в файл и читать обратно.