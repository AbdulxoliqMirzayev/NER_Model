# NER_Model

# Uz_NER: O'zbek Tilida Nomlangan Entitetlarni Aniqlash

## 📌 Loyiha haqida
**Uz_NER** - bu O'zbek tilida nomlangan entitetlarni aniqlash (NER) modeli bo'lib, matnlardagi shaxslar, joylar, tashkilotlar va boshqa muhim tushunchalarni avtomatik tarzda belgilaydi. Ushbu loyiha XLM-RoBERTa modelidan foydalanib, O'zbek tilida NER vazifasini bajarishga mo'ljallangan.

## 🚀 O'rnatish va Ishga Tushirish
Loyihani ishga tushirish uchun quyidagi talablarni bajarishingiz kerak.

### 1. Muhitni tayyorlash
Python virtual muhiti yoki conda muhitidan foydalanishni tavsiya etamiz:
```bash
python3 -m venv uz_ner_env
source uz_ner_env/bin/activate  # Linux/Mac
uz_ner_env\Scripts\activate  # Windows
```

### 2. Kerakli kutubxonalarni o‘rnatish
Loyihada foydalaniladigan kutubxonalarni quyidagi buyruq bilan o‘rnating:
```bash
pip install -r requirements.txt
```
Agar `requirements.txt` fayli mavjud bo'lmasa, quyidagi kutubxonalarni o‘rnating:
```bash
pip install torch transformers datasets huggingface_hub gradio numpy pandas tqdm
```

### 3. Modelni yuklab olish
O'qitilgan modelni Hugging Face Hub dan yuklab olish:
```python
from transformers import AutoModelForTokenClassification, AutoTokenizer

model_name = "AbdulxoliqMirzaev/roberta-ner-uz"
model = AutoModelForTokenClassification.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)
```

### 4. Modelni sinash
```python
text = "Toshkent O'zbekistonning poytaxti."
inputs = tokenizer(text, return_tensors="pt")
outputs = model(**inputs)
print(outputs)
```

## 📊 Ma'lumotlar to‘plami
Model **O‘zbek tilidagi NER ma'lumotlar to‘plami** bilan o‘qitilgan.
Bu to‘plam quyidagi teglardan iborat:
- **B-PERSON** – Shaxs nomlari
- **B-ORG** – Tashkilot nomlari
- **B-LOC** – Geografik joy nomlari
- **B-DATE** – Sanalar
- **B-PERCENT** – Foizlar

## 📂 Foydalanish
Loyihani interfeys orqali sinab ko'rish uchun **Gradio** kutubxonasidan foydalanishingiz mumkin:
```python
import gradio as gr

def ner_prediction(text):
    inputs = tokenizer(text, return_tensors="pt")
    outputs = model(**inputs)
    return outputs

iface = gr.Interface(fn=ner_prediction, inputs="text", outputs="text")
iface.launch()
```

## 📜 Litsenziya
Ushbu loyiha **MIT** litsenziyasi ostida tarqatilgan. Uni erkin foydalanishingiz va rivojlantirishingiz mumkin.

## 👨‍💻 Muallif
Loyiha **Abdulxoliq Mirzaev** tomonidan ishlab chiqilgan va **Hugging Face Hub**da joylashtirilgan --> AbdulxoliqMirzaev/roberta-ner-uz.

📬 **Aloqa:** [Hugging Face Profil](https://huggingface.co/AbdulxoliqMirzaev)

