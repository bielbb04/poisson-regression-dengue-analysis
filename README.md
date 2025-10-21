# Anàlisi Estadística de la Incidència del Dengue

Projecte d'estadística que analitza la relació entre factors climàtics i la incidència del dengue al municipi de Bello (Colòmbia) durant el període 2012-2017.

## 📋 Descripció

Aquest treball implementa una regressió de Poisson des de zero utilitzant l'algoritme de Newton-Raphson per modelar la incidència del dengue en funció de variables climàtiques. L'anàlisi inclou estadística descriptiva, contrastos d'hipòtesis i validació de models.

## 🔬 Variables Analitzades

- **Variable resposta (Y)**: Incidència del dengue
- **Variables predictores**:
  - **X1 (Tavg)**: Temperatura mitjana a 2 metres d'altura
  - **X2 (Havg)**: Humitat mitjana a 2 metres d'altura
  - **X3 (WSavg)**: Velocitat mitjana del vent a 2 metres d'altura

## 📊 Metodologia

### Anàlisi Descriptiva
- Estadístiques descriptives (mitjana, mediana, variància, mínim, màxim)
- Diagrames de caixa per any
- Anàlisi de proporcions de zeros

### Inferència Estadística
- Test de normalitat (Shapiro-Wilk)
- Contrast d'hipòtesis per comparació de mitjanes
- Test d'ajust a distribució de Poisson (Chi-quadrat)

### Regressió de Poisson
Implementació manual de l'algoritme de Newton-Raphson per trobar els estimadors de màxima versemblança:

$$\lambda_i = \exp(\beta_0 + \beta_1 x_{i1} + \beta_2 x_{i2} + \beta_3 x_{i3})$$

**Algoritme iteratiu:**
$$\vec{\beta}_{k+1} = \vec{\beta}_k - (H_K(\vec{\beta}_k))^{-1} \cdot \nabla K(\vec{\beta}_k)$$

## 🛠️ Tecnologies

- **R** (versió ≥ 4.0)
- Paquets utilitzats:
  - `readxl` - Lectura de fitxers Excel
  - `dplyr` - Manipulació de dades
  - `MASS` - Estimació de distribucions
  - `stats` - Tests estadístics

## 📁 Estructura del Projecte

```
.
├── README.md
├── solucions_treball_estadística.Rmd
├── DadesPractica.xlsx
└── figures/
```

## 🚀 Ús

1. Clona el repositori:
```bash
git clone https://github.com/usuari/poisson-regression-dengue-climate.git
cd poisson-regression-dengue-climate
```

2. Assegura't que tens les dades (`DadesPractica.xlsx`) al directori arrel.

3. Obre el fitxer `.Rmd` amb RStudio i executa:
```r
# Instal·lar paquets necessaris
install.packages(c("readxl", "dplyr", "MASS"))

# Executar l'anàlisi
rmarkdown::render("solucions_treball_estadística.Rmd")
```

## 📈 Resultats Principals

### Coeficients del Model (β)
- **β₀**: -1.016 (Intercepció)
- **β₁**: 0.391 (Temperatura)
- **β₂**: -0.038 (Humitat)
- **β₃**: -0.756 (Velocitat del vent)

### Interpretació
- La temperatura té un efecte positiu en la incidència del dengue
- La humitat i la velocitat del vent tenen efectes negatius
- Els resultats de la implementació manual coincideixen amb la funció `glm()` de R

## ✅ Validació

El model implementat manualment amb Newton-Raphson ha estat validat comparant-lo amb la funció `glm()` de R, obtenint resultats idèntics.

## 📝 Notes Tècniques

- El fitxer està en format R Markdown (`.Rmd`)
- Es pot generar un PDF amb `pdf-engine: pdflatex`
- L'algoritme inclou controls d'estabilitat numèrica
- Filtratge de dades: Municipi de Bello, anys 2012-2017

## 👥 Autors

Projecte realitzat per a l'assignatura 20581 - Estadística  
Universitat de les Illes Balears

## 📄 Llicència

Aquest projecte és material acadèmic de la UIB.

---

**Nota**: Aquest és un projecte educatiu que demostra la implementació d'un model de regressió de Poisson des dels fonaments matemàtics fins a la implementació pràctica en R.
