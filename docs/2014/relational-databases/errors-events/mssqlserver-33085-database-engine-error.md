---
title: MSSQLSERVER_33085 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fa7b45227050af057a5e5005a6664c973855b040
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421028"
---
# <a name="mssqlserver33085"></a>MSSQLSERVER_33085
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|33085|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND|  
|Texte du message|Une ou plusieurs méthodes restent introuvables dans la bibliothèque du fournisseur de services de chiffrement '%.*ls'.|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu utiliser le fournisseur de services de chiffrement répertorié dans le message d’erreur. Le fournisseur de services de chiffrement n'a pas pris en charge une méthode requise. L'état de l'erreur indique quelle méthode était introuvable.  
  
|État|Description|  
|-----------|-----------------|  
| 1|SqlCryptInitializeProvider|  
|2|SqlCryptFreeProvider|  
|3|SqlCryptOpenSession|  
|4|SqlCryptCloseSession|  
|5|SqlCryptGetProviderInfo|  
|6|SqlCryptGetNextAlgorithmId|  
|7|SqlCryptGetAlgorithmInfo|  
|8|SqlCryptCreateKey|  
|9|SqlCryptDropKey|  
|10|SqlCryptGetNextKeyId|  
|11|SqlCryptGetKeyInfoByKeyId|  
|12|SqlCryptGetKeyInfoByThumb|  
|13|SqlCryptGetKeyInfoByName|  
|14|SqlCryptExportKey|  
|15|SqlCryptImportKey|  
|16|SqlCryptEncrypt|  
|17|SqlCryptDecrypt|  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Contactez le fournisseur de services de chiffrement pour plus d'informations.  
  
  
