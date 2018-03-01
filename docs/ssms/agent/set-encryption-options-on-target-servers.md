---
title: "Définir des options de chiffrement sur des serveurs cibles | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a7a7204e78c23ef6a4c5309f0c8f45d756f740fb
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="set-encryption-options-on-target-servers"></a>Définir des options de chiffrement sur des serveurs cibles
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Si vous ne pouvez pas utiliser de certificat pour les communications chiffrées SSL (Secure Sockets Layer) entre des serveurs maîtres et tous ou une partie de vos serveurs cibles, mais que vous souhaitez chiffrer le canal entre ces serveurs, configurez le serveur cible de façon à utiliser le niveau de sécurité requis.  
  
Pour configurer le niveau de sécurité approprié requis pour un canal de communication spécifique serveur maître/serveur cible, affectez à la sous-clé de Registre [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*nom_instance*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** sur le serveur cible l’une des valeurs suivantes. La valeur de \<*nom_instance*> est **MSSQL.***n*. Par exemple, **MSSQL.1** ou **MSSQL.3**.  
  
|Valeur|Description|  
|---------|---------------|  
|**0**|Désactive le chiffrement entre ce serveur cible et le serveur maître. Ne choisissez cette option que lorsque le canal entre le serveur cible et le serveur maître est sécurisé par d'autres moyens.|  
|**1**|Active le chiffrement uniquement entre ce serveur cible et le serveur maître, mais aucune validation de certificat n'est requise.|  
|**2**|Active le chiffrement SSL et la validation de certificat complets entre ce serveur cible et le serveur maître. Il s’agit du paramètre par défaut. Sauf si vous avez une raison particulière de choisir une valeur différente, nous vous recommandons de ne pas le modifier.|  
  
Si **1** ou **2** est spécifié, le protocole SSL doit être activé sur les serveurs maîtres et cibles. Si **2** est spécifié, un certificat signé correctement doit également être présent sur le serveur maître.  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry_md.md)]  
  
## <a name="see-also"></a> Voir aussi  
[Procédure : activer des connexions chiffrées dans le moteur de base de données (Gestionnaire de configuration SQL Server)](http://msdn.microsoft.com/en-us/e1e55519-97ec-4404-81ef-881da3b42006)  
  
