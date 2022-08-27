# Solución para el error cURL error 7: (see https://curl.haxx.se/libcurl/c/libcurl-errors.html) for https://api-app-proteco.herokuapp.com/courses o similares.

Si en algun momento se encutran con este error al querer entrar a las opciones para la publicación de contenido en la página web.

![image](https://user-images.githubusercontent.com/42527034/187046966-bbe08959-5a62-4af1-89d7-1ddb2dd2421b.png)

La solución es la siguiente:

Entrar por SSH al servidor de PROTECO (pedir las credenciales a los responsables del servidor).

![image](https://user-images.githubusercontent.com/42527034/187047020-601946d9-d31c-4c26-97b5-3258f8e8eadb.png)

Ejecutar el comando **getsebool -a | grep httpd** y buscar el regitro **httpd_can_network_connect** y verificar que se tenga el valor de **off**

![image](https://user-images.githubusercontent.com/42527034/187047074-5132da22-36fa-4b24-8f1c-eb442080a696.png)

Cambiar el valor del registro a true con el comando **sudo setsebool httpd_can_network_connect true**.

![image](https://user-images.githubusercontent.com/42527034/187047226-6025a448-d8a8-4b33-8b13-6cdf7c8ec784.png)

Reiniciar el servicio **httpd** con **sudo systemctl restrat httpd**.

![image](https://user-images.githubusercontent.com/42527034/187047231-a64b848b-3dc8-427a-99df-49552cf0bbc6.png)

Verificar que el valor del registro se haya cambiado correctamente.

![image](https://user-images.githubusercontent.com/42527034/187047254-5c29b0d4-21d4-4e91-a528-abe418e538fb.png)

Finalmente, tratar de ingresar a la página Web.

![image](https://user-images.githubusercontent.com/42527034/187047280-521451c2-780d-48c9-93a3-9bcf1412210c.png)

## Referencia
[1] Reverse Proxy with Apache on Centos 6 (https://stackoverflow.com/questions/25055008/reverse-proxy-with-apache-on-centos-6)

