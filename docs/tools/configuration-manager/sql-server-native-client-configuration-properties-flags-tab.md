---
title: "Propriétés de Configuration SQL Server Native Client (onglet indicateurs) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a5d9175bba7e492ad2844803a8ce7fe1e6c09034
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a>Propriétés de la configuration de SQL Server Native Client (onglet Indicateurs)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur cet ordinateur, les clients communiquent avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveurs à l’aide des protocoles fournis dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier de bibliothèque Native Client. Cette page permet de configurer l'ordinateur client de manière à ce qu'il demande une connexion chiffrée utilisant le protocole SSL (Secure Sockets Layer). En cas d'impossibilité d'établir une connexion chiffrée, la connexion échoue.  
  
 Le processus de connexion est toujours chiffré. Les options ci-dessous s'appliquent uniquement aux données de chiffrement. Pour plus d’informations sur la manière dont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chiffre les communications et pour obtenir des instructions sur la manière de configurer le client pour qu’il approuve l’autorité racine du certificat du serveur, consultez « Chiffrement des connexions à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]» et « Activer les connexions chiffrées dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)] (Gestionnaire de configuration[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) » dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Options  
 **Forcer le chiffrement du protocole**  
 Demande une connexion utilisant le protocole SSL.  
  
 **Faire confiance au certificat de serveur**  
 Quand cette option a la valeur **Non**, le processus client tente de valider le certificat du serveur. Le client et le serveur doivent tous les deux posséder un certificat émanant d'une autorité de certification publique. Si le certificat n'est pas présent sur l'ordinateur client ou que la validation du certificat échoue, la connexion prend fin.  
  
 Quand l’option a la valeur **Oui**, le client ne valide pas le certificat du serveur, ce qui permet d’utiliser un certificat autosigné.  
  
 **Faire confiance au certificat de serveur** n’est disponible que si l’option **Forcer le chiffrement du protocole** a la valeur **Oui**.  
  
  
