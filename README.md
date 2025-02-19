# 🌟 **NURE Schedule API Documentation**

Добре структуроване та просте у використанні API для отримання розкладу занять студентів **ХНУРЕ**! 🏫

---

## 🚀 **Базовий URL**

```
https://nure-api.onrender.com
```

---

## 📚 **Ендпоїнти**

### 1. 🔍 **Отримання списку всіх груп**

**Запит:**  
```
GET /groups
```

**Опис:**  
Повертає список усіх доступних груп із їхніми ідентифікаторами.

**Приклад відповіді:**
```json
[
    {
        "group_name": "ІТШІ-24-1",
        "group_id": "11412612"
    },
    {
        "group_name": "ПЗПІ-24-5",
        "group_id": "11412133"
    }
]
```

---

### 2. 🔎 **Пошук групи за частиною назви**

**Запит:**  
```
GET /groups/search?query={частина_назви}
```

**Параметри:**  
- `query` (рядок) – частина назви групи.

**Опис:**  
Повертає список груп, у назвах яких міститься вказана частина.

**Приклад запиту:**  
```
GET /groups/search?query=ітші
```

**Приклад відповіді:**
```json
[
    {
        "group_name": "ІТШІ-24-1",
        "group_id": "11412612"
    },
    {
        "group_name": "ІТШІ-24-2",
        "group_id": "11412614"
    }
]
```

---

### 3. 📅 **Отримання розкладу для групи**

**Запит:**  
```
GET /schedule/{group_id}?start_date={дата_початку}&end_date={дата_кінця}
```

**Параметри:**  
- `group_id` (рядок) – ідентифікатор групи.  
- `start_date` (рядок) – дата початку періоду у форматі `dd.mm.yyyy`.  
- `end_date` (рядок) – дата кінця періоду у форматі `dd.mm.yyyy`.

**Опис:**  
Повертає розклад для вказаної групи за обраний період.

**Приклад запиту:**  
```
GET /schedule/11412612?start_date=01.09.2024&end_date=31.01.2025
```

**Приклад відповіді:**
```json
{
    "group": "ІТШІ-24-1",
    "schedule": [
        {
            "week": 1,
            "days": [
                {
                    "day": "Понеділок",
                    "lessons": [
                        {
                            "time": "08:30-10:05",
                            "lesson": "Програмування",
                            "type": "Лабораторна"
                        },
                        {
                            "time": "10:15-11:50",
                            "lesson": "Математика",
                            "type": "Лекція"
                        }
                    ]
                }
            ]
        }
    ]
}
```

---

## ⚙️ **Приклади використання**

### **1. Отримання списку всіх груп**
```bash
curl -X GET "https://nure-api.onrender.com/groups"
```

### **2. Пошук групи за частиною назви**
```bash
curl -X GET "https://nure-api.onrender.com/groups/search?query=ітші"
```

### **3. Отримання розкладу для групи**
```bash
curl -X GET "https://nure-api.onrender.com/schedule/11412612?start_date=01.09.2024&end_date=31.01.2025"
```

---

## 💡 **Примітки**

1. 🗓️ **Формат дат** має бути строго `dd.mm.yyyy`.  
2. 🆕 Усі дані оновлюються у реальному часі.  
3. 🛑 У разі помилок API повертає повідомлення у форматі JSON.

---

## 📧 **Зворотній зв’язок**

Якщо у вас виникли питання або пропозиції, звертайтеся за допомогою!
