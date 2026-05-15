# PINNs — Ecuación de Hirota | Sitio Quarto

Sitio web estático generado con Quarto, listo para publicar en GitHub Pages.

---

## Estructura del proyecto

```
pinn-hirota-site/
├── _quarto.yml          ← Configuración central
├── custom.scss          ← Estilo visual (paleta del reveal.js original)
├── index.qmd            ← Portada + Motivación (Ap. 1)
├── formulacion.qmd      ← Hirota + PINN (Ap. 2)
├── calibracion.qmd      ← NLS N=1 y N=2 (Ap. 3)
├── exploracion.qmd      ← Hirota N=1, N=2 (Ap. 4)
├── fronteras.qmd        ← Estudio de BC (Ap. 5)
├── muestreo.qmd         ← Estrategias de muestreo (Ap. 6)
├── sintesis.qmd         ← Síntesis + Referencias (Ap. 7)
└── figures/             ← COLOCA AQUÍ TUS FIGURAS (ver inventario abajo)
```

---

## Inventario de figuras requeridas

Copia tus figuras en la carpeta `figures/` con exactamente estos nombres:

### Calibración (Ap. 3)
```
figures/E_loss_components_N1_50N0_50Nb_10kNf_3x40.png
figures/C_uvh_errors_N2Bound_50N0_50Nb_10kNf_3x40.png
figures/movie_NLS_N1.mp4
figures/L_solution_vs_error_N2Inter_100N0_100Nb_20kNf_4x80.mp4
```

### Exploración Hirota (Ap. 4)
```
figures/C_field_h_Hir_N2Int_5kAdam_10kFGS.png
figures/L_solution_vs_error_Hir_N2Int_5kAdam_10kFGS.mp4
figures/F_l2_spearman_bars_arquitectura_HirN2.png
figures/K_norm_conservation.png
```

### Condiciones de frontera (Ap. 5)
```
figures/BC1_loss_comparison.png
figures/BC2_residual_heatmap.png
figures/BC3_l2_instantaneous.png
figures/BC5_striae_isolines_Hir_N2Bound_Full_4x80_BC_1_No_BC.png
figures/K_norm_conservation.png          ← (la misma que Ap. 4, o una específica de Bound)
```

### Muestreo (Ap. 6)
```
figures/S1_sampling_panel_Yan.png
figures/S2_striae_comparison_Yan.png
figures/H_spearman_scatter_Hir_N1_5x40_LHS_10kAdam_10kFGS_Yan.png
figures/F_l2_bars_Yan.png
figures/S1_sampling_panel_Bound.png
figures/F_l2_bars_Bound.png
figures/S2_striae_comparison_Bound.png
figures/K_norm_conservation_Bound.png
```

> **Nota sobre videos:** Los MP4 quedan embebidos con `<video>` nativo.
> Si prefieres no incluirlos en el sitio estático, borra esas secciones en los .qmd.

---

## Instalación de Quarto

1. Descarga e instala Quarto desde https://quarto.org/docs/get-started/
2. Verifica la instalación:
   ```bash
   quarto --version
   ```

---

## Pasos para publicar en GitHub Pages

### Paso 1 — Preparar el repositorio local

```bash
# Navega a la carpeta del proyecto
cd pinn-hirota-site

# Copia tus figuras en figures/
# (ver inventario arriba)

# Verifica que el sitio compila localmente
quarto preview
```

El navegador abrirá una vista previa en `http://localhost:XXXX`.

### Paso 2 — Renderizar el sitio

```bash
quarto render
```

Esto genera la carpeta `docs/` con todos los HTML estáticos.

### Paso 3 — Crear repositorio en GitHub

1. Ve a https://github.com/new
2. Crea un repositorio público, por ejemplo: `pinn-hirota`
3. NO inicialices con README (lo haremos nosotros)

### Paso 4 — Subir el proyecto

```bash
git init
git add .
git commit -m "Sitio Quarto PINNs Hirota - versión inicial"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/pinn-hirota.git
git push -u origin main
```

### Paso 5 — Configurar GitHub Pages

1. En tu repositorio de GitHub, ve a **Settings → Pages**
2. En **Source**, selecciona:
   - Branch: `main`
   - Folder: `/docs`
3. Haz clic en **Save**
4. En ~2 minutos, tu sitio estará en:
   `https://TU_USUARIO.github.io/pinn-hirota`

### Paso 6 — Actualizar el enlace en `_quarto.yml`

Edita `_quarto.yml` y reemplaza `TU_USUARIO`:
```yaml
navbar:
  right:
    - icon: github
      href: https://github.com/TU_USUARIO/pinn-hirota
```

---

## Flujo de trabajo para actualizaciones

Cada vez que modifiques figuras o texto:

```bash
quarto render          # Re-genera docs/
git add .
git commit -m "Actualización: descripción del cambio"
git push
```

GitHub Pages se actualiza automáticamente en ~1 minuto.

---

## Lightbox (zoom en figuras)

El lightbox está activado globalmente. Al hacer clic en cualquier figura,
se abre en pantalla completa. Las figuras agrupadas (mismo `group=`) permiten
navegar entre ellas con las flechas. No requiere configuración adicional.

---

## Notas de diseño

- **Paleta de colores:** idéntica a la presentación reveal.js original
- **Figuras:** tamaño máximo, centradas, con sombra y efecto hover
- **Cajas de hallazgo/hipótesis:** mismos estilos que la presentación
- **Tablas:** misma paleta (encabezado azul-medio, filas alternadas)
- **Ecuaciones:** MathJax con la misma configuración del HTML original
- **Responsive:** el layout de dos columnas colapsa a una en móvil

---

## Posibles problemas

| Problema | Solución |
|----------|----------|
| Las figuras no aparecen | Verifica que estén en `figures/` con el nombre exacto |
| Los videos no reproducen | Asegúrate de que los MP4 estén en `figures/` |
| Las ecuaciones no renderizan | Espera a que MathJax cargue (requiere conexión) |
| GitHub Pages no actualiza | Espera 2-5 min después del push |
| Error de compilación Quarto | Revisa la sintaxis del .qmd afectado con `quarto preview` |
