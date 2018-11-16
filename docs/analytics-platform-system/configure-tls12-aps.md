---
title: 'Configuration TLS 1.2 dans Analytique Platform System | Microsoft Docs '
description: Recommandation pour configurer TLS 1.2 dans APS
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 15bee3f68bf922ec9220c9ac570e5bd372f47483
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51697857"
---
# <a name="configure-tls-12-in-aps"></a>Configurer TLS 1.2 dans APS

Pour sécuriser les points d’accès pour utiliser uniquement TLS 1.2, vous devrez désactiver explicitement d’autres protocoles sur tous les hôtes physiques et virtuels. La désactivation des protocoles nécessitent des modifications de paramètre de Registre.

> [!WARNING]
> Cette section, méthode ou tâche contient les étapes qui vous indiquent comment modifier le Registre. Toutefois, les problèmes graves peuvent survenir si vous modifiez le Registre incorrecte qui peut entraîner une perte de données et nécessiter la réinstallation du système d’exploitation. Nous recommandons vivement sauvegarder le Registre avant de le modifier. De cette manière, vous pourrez restaurer le Registre si un problème survient. Pour plus d’informations sur la façon de sauvegarder et restaurer le Registre, cliquez sur le numéro d’article suivant pour afficher l’article dans la Base de connaissances Microsoft :<br>
[322756](https://support.microsoft.com/help/322756) comment sauvegarder et restaurer le Registre dans Windows

**Désactiver :**
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
```

Également définir les clés suivantes sur votre client ordinateurs où sont installés les outils tels que les adaptateurs de destination APS SSIS.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



