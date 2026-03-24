# RANKDOWN 

**The Niche Knowledge Party Game** — guess ranked items, score points equal to the rank number.

## File Structure

```
index.html
data/
  countries_population.csv   (100 items)
  countries_area.csv         (100 items)
  ...
```

## Deploy to GitHub Pages

1. Create a new GitHub repo (e.g. `rankdown`)
2. Upload **all files** keeping the `data/` folder structure
3. Go to **Settings → Pages → Source: Deploy from branch → main / (root)**
4. Your game is live at `https://<username>.github.io/rankdown`

## Local Testing

Because the game loads CSVs via `fetch()`, you need a local web server:

```bash
# Python 3
python -m http.server

# Node
npx serve .

# Then open http://localhost:8000
```

> Opening `index.html` directly as a `file://` URL will NOT work.

## Adding New Categories/Datasets

1. Create `data/my_category.csv` with format:
   ```
   name,value,aliases
   item 1,value1,alias1|alias2
   item 2,,value2alias1|alias2
   etc.
   ```
   The rank is determined by row order (row 1 = rank #1).

2. Add an entry to the `CATEGORIES` array in `index.html` in json format:
   ```js
   {
     id: "my_cat",
     name: "My Category Name",
     emoji: "🎯",
     file: "data/my_category.csv",
     metric: "Short description of the metric",
     valueLabel: "Something like Population"
     valueFmt: "population/number/decimal/"
     tip: "A hint for players about what's surprising in this list."
   }
   ```
