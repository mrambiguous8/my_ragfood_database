# RAG Food System – Customised by Dennis Bonnici

This is my enhanced version of the RAG-Food project. I added 43 food items focused on:
- Filipino / cultural cuisine
- Healthy foods with detailed nutrition benefits
- Popular international dishes with cooking methods

# List of 43 Food Items
Adobo — Savory, tangy braised meat
Sinigang — Tangy sour vegetable soup
Kare-Kare — Creamy peanut meat stew
Lechon — Whole roasted crispy pork
Pancit Canton — Stir-fried savory wheat noodles
Halo-Halo — Shaved ice dessert medley
Laing — Spicy coconut taro leaves
Bibingka — Festive baked rice cake
Chicken Inasal — Citrus-marinated grilled chicken
Taho — Warm silken tofu snack
Quinoa Kale Bowl — Nutritious quinoa kale bowl
Grilled Salmon with Broccolini — Omega-3 salmon and broccolini
Lentil and Vegetable Stew — Hearty lentil vegetable stew
Greek Yogurt Parfait — Layered yogurt fruit parfait
Tofu Stir-Fry with Brown Rice — Crispy tofu, brown rice
Chickpea and Avocado Salad — Chickpea avocado lemon salad
Baked Sweet Potato with Cottage Cheese — Sweet potato with cheese
Spinach and Mushroom Omelet — Spinach mushroom egg omelet
Berry Oat Smoothie — Berry oat breakfast smoothie
Roasted Beet and Goat Cheese Salad — Roasted beet goat-cheese salad
Miso Soup with Seaweed and Tofu — Umami miso seaweed tofu soup
Margherita Pizza — Classic tomato mozzarella pizza
Sushi (Nigiri and Maki) — Fresh rice and fish
Tacos al Pastor — Spit-roasted pork tacos
Butter Chicken (Murgh Makhani) — Creamy spiced tomato chicken
Pad Thai — Sweet-sour stir-fried rice noodles
Peking Duck — Crispy lacquered roast duck
Coq au Vin — Wine-braised chicken stew
Fish and Chips — Battered fish with chips
Falafel Wrap — Spiced chickpea fritters wrap
Bibimbap — Mixed rice vegetable bowl
Paella Valenciana — Saffron rice with meats
Tagine with Apricots and Almonds — Sweet-spiced lamb tagine
Jollof Rice — Tomato-pepper seasoned rice
Pho — Aromatic clear noodle soup
Shakshuka — Poached eggs in tomato
Ceviche — Citrus-cured fresh fish
Ratatouille — Stewed summer vegetables medley
Kimchi Fried Rice — Spicy fermented kimchi rice
Baklava — Layered nut pastry
Pasta Carbonara — Creamy egg cheese pasta
Hamburger — Grilled beef patty sandwich
Feijoada — Hearty black bean stew

---

## 📄 `README.md`

````markdown
# 🧠 RAG-Food: Simple Retrieval-Augmented Generation with ChromaDB + Ollama

This is a **minimal working RAG (Retrieval-Augmented Generation)** demo using:

- ✅ Local LLM via [Ollama](https://ollama.com/)
- ✅ Local embeddings via `mxbai-embed-large`
- ✅ [ChromaDB](https://www.trychroma.com/) as the vector database
- ✅ A simple food dataset in JSON (Filipino foods, fruits, etc.)

---

## 🎯 What This Does

This app allows you to ask questions like:

- “Which foods include chickpeas?”
- “What dessert is made from milk and cream?”
- “What is Halo-Halo made of and what are its main ingredients?”

It **does not rely on the LLM’s built-in memory**. Instead, it:

1. **Embeds your custom text data** (about food) using `mxbai-embed-large`
2. Stores those embeddings in **ChromaDB**
3. For any question, it:
   - Embeds your question
   - Finds relevant context via similarity search
   - Passes that context + question to a local LLM (`llama3.2`)
4. Returns a natural-language answer grounded in your data.

---

## 📦 Requirements

### ✅ Software

- Python 3.8+
- Ollama installed and running locally
- ChromaDB installed

### ✅ Ollama Models Needed

Run these in your terminal to install them:

```bash
ollama pull llama3.2
ollama pull mxbai-embed-large
````

> Make sure `ollama` is running in the background. You can test it with:
>
> ```bash
> ollama run llama3.2
> ```

---

## 🛠️ Installation & Setup

### 1. Clone or download this repo

```bash
git clone https://github.com/mrambiguous8/my_ragfood_database
cd rag-food
```

### 2. Install Python dependencies

```bash
pip install chromadb requests
```

### 3. Run the RAG app

```bash
python rag_run.py
```

If it's the first time, it will:

* Create `fooddatabase.json` if missing
* Generate embeddings for all food items
* Load them into ChromaDB
* Run a few example questions

---

## 📁 File Structure

```
ragfood_database/
├── rag_run.py        # Main app script
├── fooddatabase.json # Food knowledge base (created if missing)
├── README.md         # This file
```

---

## 🧠 How It Works (Step-by-Step)

1. **Data** is loaded from `fooddatabase.json`
2. Each entry is embedded using Ollama's `mxbai-embed-large`
3. Embeddings are stored in ChromaDB
4. When you ask a question:

   * The question is embedded
   * The top 1–2 most relevant chunks are retrieved
   * The context + question is passed to `llama3.2`
   * The model answers using that info only

---

## 🔍 Try Custom Questions

You can update `rag_run.py` to include your own questions like:

```python
print(rag_query("What is Adobo?"))
print(rag_query("Which foods are vegetarian?"))
```

---

## 🚀 Next Ideas

* Swap in larger datasets (Wikipedia articles, recipes, PDFs)
* Add a web UI with Gradio or Flask
* Cache embeddings to avoid reprocessing on every run

---

## 👨‍🍳 Credits


This project is based upon RAG-Food repository https://github.com/gocallum/ragfood by Callum Bir using the following: 

* [Ollama](https://ollama.com)
* [ChromaDB](https://www.trychroma.com)
* [mxbai-embed-large](https://ollama.com/library/mxbai-embed-large)
* Filipino food inspiration 🍛

