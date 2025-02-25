---
title: Configurar un dominio personalizado para tu sitio de Páginas de GitHub
intro: 'Puedes configurar o actualizar determinados registros DNS y las configuraciones de tu repositorio para que apunten el dominio predeterminado de tu sitio de {% data variables.product.prodname_pages %} a un dominio personalizado.'
redirect_from:
  - /articles/quick-start-setting-up-a-custom-domain
  - /articles/setting-up-an-apex-domain
  - /articles/setting-up-a-www-subdomain
  - /articles/setting-up-a-custom-domain
  - /articles/setting-up-an-apex-domain-and-www-subdomain
  - /articles/adding-a-cname-file-to-your-repository
  - /articles/setting-up-your-pages-site-repository
  - /articles/managing-a-custom-domain-for-your-github-pages-site
  - /github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site
product: '{% data reusables.gated-features.pages %}'
versions:
  fpt: '*'
  ghec: '*'
topics:
  - Pages
shortTitle: Manage a custom domain
ms.openlocfilehash: ad96d0be88614e8294e29de74fd7112cfed1bc46
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '147710327'
---
Las personas con permisos de administración para un repositorio pueden configurar un dominio personalizado para un sitio de {% data variables.product.prodname_pages %}.

## Acerca de la configuración de dominios personalizados

Asegúrate de agregar tu dominio personalizado al sitio de {% data variables.product.prodname_pages %} antes de configurar el dominio personalizado con tu proveedor DNS. Configurar tu dominio personalizado con tu proveedor DNS sin agregar tu dominio personalizado a {% data variables.product.product_name %} podría dar como resultado que alguien aloje un sitio en uno de tus subdominios.

{% windows %}

El comando `dig`, que se puede usar para verificar la correcta configuración de los registros DNS, no está incluido en Windows. Para comprobar que los registros DNS se han configurado correctamente, debes instalar [BIND](https://www.isc.org/bind/).

{% endwindows %}

{% note %}

**Nota:** Los cambios de DNS pueden tardar hasta 24 horas en propagarse.

{% endnote %}

## Configurar un subdominio

Para configurar un `www` o subdominio personalizado, como `www.example.com` o `blog.example.com`, debes agregar el dominio en la configuración del repositorio. Después de esto, configura un registro de CNAME con tu proveedor de DNS.

{% data reusables.pages.navigate-site-repo %} {% data reusables.repositories.sidebar-settings %} {% data reusables.pages.sidebar-pages %}
4. En "Dominio personalizado", escribe el nombre de tu dominio personalizado y, a continuación, haz clic en **Guardar**. Si publicas el sitio desde una rama, se creará una confirmación que agrega un archivo `CNAME` a la raíz de la rama de origen. Si publicas el sitio con un flujo de trabajo de {% data variables.product.prodname_actions %} personalizado, no se crea ningún archivo `CNAME`. Para más información sobre la fuente de publicación, consulta "[Configuración de una fuente de publicación para el sitio de GitHub Pages](/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)."
  ![Botón de guardar dominio personalizado](/assets/images/help/pages/save-custom-subdomain.png)
5. Desplázate hasta tu proveedor DNS y crea un registro `CNAME` que apunte tu subdominio al dominio predeterminado de tu sitio. Por ejemplo, si quieres usar el subdominio `www.example.com` para el sitio de usuario, crea un registro `CNAME` que dirija `www.example.com` a `<user>.github.io`. Si quieres usar el subdominio `another.example.com` para el sitio de la organización, crea un registro `CNAME` que dirija `another.example.com` a `<organization>.github.io`. El registro `CNAME` siempre debe apuntar a `<user>.github.io` o `<organization>.github.io`, excepto el nombre del repositorio. {% data reusables.pages.contact-dns-provider %} {% data reusables.pages.default-domain-information %}

{% indented_data_reference reusables.pages.wildcard-dns-warning spaces=3 %} {% data reusables.command_line.open_the_multi_os_terminal %}
6. Para confirmar que el registro DNS se ha configurado correctamente, usa el comando `dig` y reemplaza _WWW.EXAMPLE.COM_ por el subdominio.
```shell
    $ dig <em>WWW.EXAMPLE.COM</em> +nostats +nocomments +nocmd
    > ;<em>WWW.EXAMPLE.COM.</em>                     IN      A
    > <em>WWW.EXAMPLE.COM.</em>              3592    IN      CNAME   <em>YOUR-USERNAME</em>.github.io.
    > <em>YOUR-USERNAME</em>.github.io.      43192   IN      CNAME   <em> GITHUB-PAGES-SERVER </em>.
    > <em> GITHUB-PAGES-SERVER </em>.         22      IN      A       192.0.2.1
```
{% data reusables.pages.build-locally-download-cname %} {% data reusables.pages.enforce-https-custom-domain %}

## Configurar un dominio apex

Para configurar un dominio apex, como `example.com`, debes configurar un dominio personalizado en la configuración del repositorio y al menos un registro `ALIAS`, `ANAME` o `A` con el proveedor de DNS.

{% data reusables.pages.www-and-apex-domain-recommendation %} Para obtener más información, consulta "[Configuración de un subdominio](#configuring-a-subdomain)".

{% data reusables.pages.navigate-site-repo %} {% data reusables.repositories.sidebar-settings %} {% data reusables.pages.sidebar-pages %}
4. En "Dominio personalizado", escribe el nombre de tu dominio personalizado y, a continuación, haz clic en **Guardar**. Si publicas el sitio desde una rama, se creará una confirmación que agrega un archivo `CNAME` a la raíz de la rama de origen. Si publicas el sitio con un flujo de trabajo de {% data variables.product.prodname_actions %} personalizado, no se crea ningún archivo `CNAME`. Para más información sobre la fuente de publicación, consulta "[Configuración de una fuente de publicación para el sitio de GitHub Pages](/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)."
  ![Botón de guardar dominio personalizado](/assets/images/help/pages/save-custom-apex-domain.png)
5. Desplázate hasta el proveedor DNS y crea un registro `ALIAS`, `ANAME` o `A`. También puedes crear registros `AAAA` para la compatibilidad con IPv6. {% data reusables.pages.contact-dns-provider %}
    - Para crear un registro `ALIAS` o `ANAME`, apunta el dominio apex al dominio predeterminado del sitio. {% data reusables.pages.default-domain-information %}
    - Para crear registros `A`, apunta el dominio apex a las direcciones IP de {% data variables.product.prodname_pages %}.
      ```shell
      185.199.108.153
      185.199.109.153
      185.199.110.153
      185.199.111.153
      ```
    - Para crear registros `AAAA`, apunta el dominio apex a las direcciones IP de {% data variables.product.prodname_pages %}.
      ```shell
      2606:50c0:8000::153
      2606:50c0:8001::153
      2606:50c0:8002::153
      2606:50c0:8003::153
      ```

{% indented_data_reference reusables.pages.wildcard-dns-warning spaces=3 %} {% data reusables.command_line.open_the_multi_os_terminal %}
6. Para confirmar que el registro DNS se ha configurado correctamente, usa el comando `dig`, reemplazando _EXAMPLE.COM_ por tu dominio apex. Confirma que los resultados coincidan con las direcciones IP de las {% data variables.product.prodname_pages %} que aparecen arriba.
   - Para registros `A`.
    ```shell
    $ dig <em>EXAMPLE.COM</em> +noall +answer -t A
    > <em>EXAMPLE.COM</em>     3600    IN A     185.199.108.153
    > <em>EXAMPLE.COM</em>     3600    IN A     185.199.109.153
    > <em>EXAMPLE.COM</em>     3600    IN A     185.199.110.153
    > <em>EXAMPLE.COM</em>     3600    IN A     185.199.111.153
    ```
   - Para registros `AAAA`.
    ```shell
    $ dig <em>EXAMPLE.COM</em> +noall +answer -t AAAA
    > <em>EXAMPLE.COM</em>     3600    IN AAAA     2606:50c0:8000::153
    > <em>EXAMPLE.COM</em>     3600    IN AAAA     2606:50c0:8001::153
    > <em>EXAMPLE.COM</em>     3600    IN AAAA     2606:50c0:8002::153
    > <em>EXAMPLE.COM</em>     3600    IN AAAA     2606:50c0:8003::153
    ```
{% data reusables.pages.build-locally-download-cname %} {% data reusables.pages.enforce-https-custom-domain %}

## Configuración de un dominio apex y la variante de subdominio `www`

Cuando utilizas un dominio apex, te recomendamos configurar tu sitio de {% data variables.product.prodname_pages %} para hospedar contenido tanto en el dominio de apex como en la variante de subdominio `www`.

Para configurar un subdominio `www` junto con el dominio apex, primero debes configurar un dominio apex mediante la creación de un registro `ALIAS`, `ANAME` o `A` con el proveedor DNS. Para obtener más información, consulta "[Configuración de un dominio apex](#configuring-an-apex-domain)".

Después de configurar el domnio apex, debes configurar un registro de CNAME con tu proveedor de DNS.

1. Desplázate hasta tu proveedor DNS y crea un registro `CNAME` que apunte `www.example.com` al dominio predeterminado de tu sitio: `<user>.github.io` o `<organization>.github.io`. No incluyas el nombre de repositorio. {% data reusables.pages.contact-dns-provider %} {% data reusables.pages.default-domain-information %}
2. Para confirmar que el registro DNS se ha configurado correctamente, usa el comando `dig` y reemplaza _WWW.EXAMPLE.COM_ por la variante de subdominio `www`.
```shell
    $ dig <em>WWW.EXAMPLE.COM</em> +nostats +nocomments +nocmd
    > ;<em>WWW.EXAMPLE.COM.</em>                     IN      A
    > <em>WWW.EXAMPLE.COM.</em>              3592    IN      CNAME   <em>YOUR-USERNAME</em>.github.io.
    > <em>YOUR-USERNAME</em>.github.io.      43192   IN      CNAME   <em> GITHUB-PAGES-SERVER </em>.
    > <em> GITHUB-PAGES-SERVER </em>.         22      IN      A       192.0.2.1
```
## Eliminar un dominio personalizado

{% data reusables.pages.navigate-site-repo %} {% data reusables.repositories.sidebar-settings %} {% data reusables.pages.sidebar-pages %}
4. En "Dominio personalizado", haz clic en **Quitar**.
  ![Botón de guardar dominio personalizado](/assets/images/help/pages/remove-custom-domain.png)

## Asegurar tu dominio personalizado

{% data reusables.pages.secure-your-domain %} Para obtener más información, consulta "[Comprobación de un dominio personalizado para {% data variables.product.prodname_pages %}](/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages)".

## Información adicional

- "[Solución de problemas de dominios personalizados y {% data variables.product.prodname_pages %}](/articles/troubleshooting-custom-domains-and-github-pages)".
