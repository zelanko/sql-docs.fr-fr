---
title: Configuration de TLS 1,2
description: Recommandation pour configurer TLS 1,2 dans APS
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 988cac765a596b541d128b0b6190f6f228d95ee7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401252"
---
# <a name="configure-tls-12-in-aps"></a>Configurer TLS 1,2 dans APS

Pour sécuriser les points d’accès afin d’utiliser uniquement TLS 1,2, vous devez désactiver explicitement le protocole sur tous les hôtes physiques et virtuels. La désactivation des protocoles nécessite des modifications de paramètres du Registre. Les modifications du Registre requièrent un redémarrage des hôtes physiques et virtuels.

> [!WARNING]
> Cette section, méthode ou tâche contient les étapes qui vous indiquent comment modifier le Registre. Toutefois, des problèmes sérieux peuvent survenir si vous modifiez le registre de manière incorrecte, ce qui peut entraîner une perte de données et nécessiter la réinstallation du système d’exploitation. Nous vous recommandons vivement de sauvegarder le registre avant de le modifier. De cette manière, vous pourrez restaurer le Registre si un problème survient. Pour plus d’informations sur la sauvegarde et la restauration du Registre, cliquez sur le numéro d’article suivant pour afficher l’article de la base de connaissances Microsoft :<br>
[322756](https://support.microsoft.com/help/322756) comment sauvegarder et restaurer le registre dans Windows

**Désactive**
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

Définissez également les clés suivantes sur vos ordinateurs clients où des outils comme les adaptateurs de destination SSIS APS sont installés.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



