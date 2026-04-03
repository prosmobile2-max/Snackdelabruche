# Outils Python pour Menus Restaurant

## Installation des bibliothèques nécessaires
```bash
pip install pillow pymupdf
```

## 1. Rogner une image (enlever du texte en bas)
```python
from PIL import Image

img = Image.open('image.png')
width, height = img.size

# Rogner 50 pixels du bas
cropped = img.crop((0, 0, width, height - 50))
cropped.save('image-rognee.png')
```

## 2. Ajouter du padding transparent autour d'une image
```python
from PIL import Image

img = Image.open('image.png')
padding = 100  # pixels de chaque côté

# Créer image avec padding
new_width = img.width + (padding * 2)
new_height = img.height + (padding * 2)
new_img = Image.new('RGBA', (new_width, new_height), (0, 0, 0, 0))
new_img.paste(img, (padding, padding))
new_img.save('image-avec-padding.png')
```

## 3. Créer une image carrée centrée
```python
from PIL import Image

img = Image.open('image.png')
target_size = 900  # taille carrée

# Calculer position pour centrer
padding_left = (target_size - img.width) // 2
padding_top = (target_size - img.height) // 2

# Créer image carrée
new_img = Image.new('RGBA', (target_size, target_size), (0, 0, 0, 0))
new_img.paste(img, (padding_left, padding_top))
new_img.save('image-carree.png')
```

## 4. Convertir PDF en PNG avec fond transparent
```python
import fitz
from PIL import Image
import io

# Désactiver limite de taille
Image.MAX_IMAGE_PIXELS = None

# Ouvrir PDF
pdf = fitz.open('logo.pdf')
page = pdf[0]

# Convertir en image
pix = page.get_pixmap(dpi=150)
img_bytes = pix.tobytes('png')
logo = Image.open(io.BytesIO(img_bytes))
logo = logo.convert('RGBA')

# Remplacer fond noir par transparent
datas = logo.getdata()
newData = []
for item in datas:
    if item[0] < 50 and item[1] < 50 and item[2] < 50:
        newData.append((255, 255, 255, 0))
    else:
        newData.append(item)

logo.putdata(newData)
logo.save('logo-transparent.png')
pdf.close()
```

## 5. Redimensionner une image
```python
from PIL import Image

img = Image.open('image.png')

# Redimensionner en gardant les proportions
img.thumbnail((500, 500))
img.save('image-petite.png')

# Ou forcer une taille exacte
img_resized = img.resize((400, 300))
img_resized.save('image-forcee.png')
```

## 6. Lancer serveur web local
```bash
# Dans le dossier du menu
python -m http.server 8000

# Puis ouvrir http://localhost:8000/index.html
```

## Notes importantes
- Toujours utiliser des images PNG avec transparence pour les produits
- Ajouter beaucoup de padding pour que les images s'affichent bien avec `object-fit: cover`
- Pour les logos, enlever le fond avec la méthode du pixel noir
- DPI 150 est suffisant pour le web (300 pour l'impression)
