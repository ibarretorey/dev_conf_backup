# Instalar mi ubuntu 0 => 100

Mas que una guía es un recordatorio de que cosas instalar, algunos archivos de configuración que conviene tenerlos en un repo mio por la dudosa estabilidad de la procedencia y una ayuda de memoria de donde se encuentran mis configuraciones y software para instalar mi devPc a mi gusto y de forma rápida y practica

## Software necesario

1. [Google chrome](https://www.google.com.mx/intl/es-419/chrome/?brand=CHBD&gclid=Cj0KCQjw3qzzBRDnARIsAECmryqQ7s8n6O1T4Sk7xO3EsdhEymfydLbIpk33SQ-heFggNLyB1YjWPqkaApLmEALw_wcB&gclsrc=aw.ds)
2. [VsCode](https://code.visualstudio.com/docs/setup/linux)
3. [Inicializar VsCode](###-Inicializar-VsCode)

### Inicializar VsCode

1. Luego de instalar VsCode, abrir el entorno e ir al menu  `vew => extensiones` , luego buscar la extension  `Settings Sync` e instalarla.
2. Sincronizar configuraciones de VsCode.
**presionar**
`ctr+shift+d`
**ó**
`ctl+shift+p`
y luego seleccionar la opción
**sync: Download Settings**
1. Ir a git, y dentro ir a => **profile** => **setting** => **depeloper settings**, generar un nuevo token para poder descargar y subir las configuraciones de vscode desde esa Pc ahora y en el futuro, copiar el token generado y pegarlo en vscode. Luego pegar el ID `dabbdddb1340119ae3181cb3ec90abd4` del gist donde están guardadas las configuraciones, the id is de last endpoint.

2. Instalar fuentes en vscode: entrar a la carpeta [FiraCodeiScript](./VsCodeFont/FiraCodeiScript/) en `./VsCodeFont/FiraCodeiScript` y luego ejecutar

```bash
copy ./FiraCodeiScript /usr/share/fonts # Para copiar las fuentes en el equipo
fc-cache -f -v # para instalar las fuentes, puede tomar unos minutos
```

## Seleccionar la guente

En visual studio code presionar `=> crtl+shift+p` y seleccionar => Preferences: Color Theme => Dark++ Italic