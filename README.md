## API de Extracción de Productos

### Descripción

Esta API en Python (`app.py`) proporciona un servicio para extraer los primeros 15 productos de una URL dada. Utiliza el método POST para recibir la URL como parámetro de entrada. La extracción de los productos se realiza mediante web scraping utilizando Selenium y BeautifulSoup.

### Requisitos

* Python 3.x
* Librerías `Flask`, `requests`, `BeautifulSoup4`, `Selenium` y `webdriver-manager`
* WebDriver para Selenium (por ejemplo, ChromeDriver)
* Docker (opcional, para la contenedorización)

### Instalación

1. Instala las dependencias:

    ```bash
    pip install Flask requests beautifulsoup4 selenium webdriver-manager
    ```

### Uso

1.  Ejecuta la API:

    ```bash
    python app.py
    ```

2.  Utiliza el script `get_api_response.py` para probar la API

    ```bash
    python get_api_response.py
    ```

### Estructura del Código

* **`app.py`**:
    * Define la API Flask con una ruta `/extract_products` que recibe una URL por POST.
    * Utiliza funciones de `utils.py` para obtener el HTML y extraer los productos.
    * Devuelve un JSON con los resultados.
* **`utils.py`**:
    * `obtener_html(url: str)`: Utiliza Selenium para obtener el HTML de la página, realizando scroll para cargar todos los productos.
    * `extract_products(html: str)`: Utiliza BeautifulSoup para parsear el HTML y extraer los nombres, precios y precios de promoción de los productos.
* **`get_api_response.py`**:
    * Script para probar la API enviando peticiones POST con URLs de prueba.

### Consideraciones Adicionales

* El script `utils.py` guarda el HTML obtenido en un archivo local para evitar consultas repetidas y posibles bloqueos.
* Se utiliza Selenium para simular el scroll y asegurar que todos los productos se carguen antes de extraer la información.
* Asegúrate de que el WebDriver sea compatible con tu navegador y esté correctamente configurado.