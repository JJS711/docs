---
title: Requerir políticas para la seguridad avanzada en tu empresa
intro: 'Puedes requerir políticas para administrar las características de {% data variables.product.prodname_GH_advanced_security %} dentro de las organizaciones de tu empresa o permitir que se configuren las políticas en cada organización.'
permissions: 'Enterprise owners can enforce policies for {% data variables.product.prodname_GH_advanced_security %} in an enterprise.'
product: '{% data reusables.gated-features.ghas %}'
versions:
  ghec: '*'
  ghes: '*'
  ghae: '*'
type: how_to
topics:
  - Advanced Security
  - Code scanning
  - Enterprise
  - Policies
  - Secret scanning
  - Security
redirect_from:
  - /admin/policies/enforcing-policies-for-advanced-security-in-your-enterprise
  - /github/setting-up-and-managing-your-enterprise/enforcing-policies-for-advanced-security-in-your-enterprise-account
  - /github/setting-up-and-managing-your-enterprise/setting-policies-for-organizations-in-your-enterprise-account/enforcing-policies-for-advanced-security-in-your-enterprise-account
shortTitle: Advanced Security policies
ms.openlocfilehash: 1858a854f78695b2fa36e0b84944f2fa05db0d00
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2022
ms.locfileid: '145116393'
---
## Acerca de las políticas para la {% data variables.product.prodname_GH_advanced_security %} en tu empresa

{% data reusables.advanced-security.ghas-helps-developers %} Para más información, vea "[Acerca de {% data variables.product.prodname_GH_advanced_security %}](/get-started/learning-about-github/about-github-advanced-security)".

{% ifversion ghes or ghec %}Si compras una licencia para la {% data variables.product.prodname_GH_advanced_security %}, cualquier{% else %}Cualquier{% endif %} organización en {% data variables.product.product_location %} podrá utilizar las características de la {% data variables.product.prodname_advanced_security %}. Puedes requerir políticas que controlen cómo los miembros de tu empresa de {% data variables.product.product_name %} utilizan la {% data variables.product.prodname_advanced_security %}.

## Requerir una política para utilizar la {% data variables.product.prodname_GH_advanced_security %} en tu empresa

{% data reusables.advanced-security.about-ghas-organization-policy %}

{% data reusables.enterprise-accounts.access-enterprise %} {% data reusables.enterprise-accounts.policies-tab %} {% data reusables.enterprise-accounts.advanced-security-policies %} {% data reusables.enterprise-accounts.advanced-security-organization-policy-drop-down %} {% data reusables.enterprise-accounts.advanced-security-individual-organization-policy-drop-down %}
