# Instrucciones para publicar en GitHub Pages

## Requisitos previos
- Tener [Quarto instalado](https://quarto.org/docs/get-started/) (versión ≥ 1.4)
- Tener Git instalado y configurado
- Cuenta en GitHub

---

## Paso 1 — Copia tus figuras a la carpeta `figures/`

Copia todos los archivos `.png`, `.mp4` y `.pdf` que genera tu postprocesamiento
a la carpeta `figures/` del proyecto. Los nombres que se esperan son:

```
figures/
  E_loss_components_N1_50N0_50Nb_10kNf_3x40.png
  movie_NLS_N1.mp4
  C_uvh_errors_N2Bound_50N0_50Nb_10kNf_3x40.png
  L_solution_vs_error_N2Inter_100N0_100Nb_20kNf_4x80.mp4
  C_field_h_Hir_N2Int_5kAdam_10kFGS.png
  L_solution_vs_error_Hir_N2Int_5kAdam_10kFGS.mp4
  F_l2_spearman_bars_arquitectura_HirN2.png
  K_norm_conservation.png
  BC1_loss_comparison.png
  BC2_residual_heatmap.png
  BC3_l2_instantaneous.png
  BC5_striae_isolines_Hir_N2Bound_Full_4x80_BC_1_No_BC.png
  S1_sampling_panel_Yan.png
  F_l2_bars_Yan.png
  S2_striae_comparison_Yan.png
  H_spearman_scatter_Hir_N1_5x40_LHS_10kAdam_10kFGS_Yan.png
  S1_sampling_panel_Bound.png
  F_l2_bars_Bound.png
  S2_striae_comparison_Bound.png
  K_norm_conservation_Bound.png
```

Si un archivo aún no existe, Quarto renderizará la página igualmente
(la imagen simplemente no aparecerá hasta que la copies).

---

## Paso 2 — Renderiza el sitio localmente (prueba)

Desde la carpeta raíz del proyecto:

```bash
quarto render
```

Esto genera la carpeta `docs/` con el sitio estático.
Para previsualizarlo en tu navegador:

```bash
quarto preview
```

---

## Paso 3 — Crea el repositorio en GitHub

1. Ve a https://github.com/new
2. Nombre sugerido: `pinn-hirota` (o el que prefieras)
3. Visibilidad: **Public** (requerido para GitHub Pages gratis)
4. No inicialices con README

---

## Paso 4 — Sube el proyecto

En la terminal, desde la carpeta del proyecto:

```bash
git init
git add .
git commit -m "Initial Quarto site: PINNs Hirota"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/pinn-hirota.git
git push -u origin main
```

Reemplaza `TU_USUARIO` con tu nombre de usuario de GitHub.

**Importante:** actualiza también el enlace en `_quarto.yml`:
```yaml
href: https://github.com/TU_USUARIO/pinn-hirota
```

---

## Paso 5 — Configura GitHub Pages

1. En tu repositorio, ve a **Settings → Pages**
2. En *Source*, selecciona:
   - Branch: `main`
   - Folder: `/docs`
3. Clic en **Save**
4. Espera ~2 minutos

Tu sitio estará disponible en:
```
https://TU_USUARIO.github.io/pinn-hirota/
```

---

## Paso 6 — Actualizar el sitio después de cambios

Cada vez que modifiques un `.qmd` o agregues figuras:

```bash
quarto render
git add .
git commit -m "Actualización: <descripción>"
git push
```

GitHub Pages se actualizará automáticamente en ~1 minuto.

---

## Notas adicionales

### Videos `.mp4`
Los videos funcionan directamente en HTML5. Solo asegúrate
de que estén en `figures/` antes de renderizar.

### Lightbox (zoom en figuras)
Ya está habilitado en `_quarto.yml` (`lightbox: true`).
Al hacer clic en cualquier imagen se abre en pantalla completa.

### Ecuaciones LaTeX
MathJax está configurado. Las ecuaciones `$...$` y `$$...$$`
se renderizan automáticamente.

### Figuras faltantes
Si al renderizar aparece una advertencia de figura no encontrada,
es normal — solo significa que aún no copiaste esa imagen.
El sitio renderiza igual.

### Tamaño del repo
Los `.mp4` pueden ser pesados. Si superan 50 MB en total,
considera usar [Git LFS](https://git-lfs.com/) o alojar
los videos en YouTube/Drive y embeber el link.
