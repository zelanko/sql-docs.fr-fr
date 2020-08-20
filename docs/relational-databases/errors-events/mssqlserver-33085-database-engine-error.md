---
description: MSSQLSERVER_33085
title: MSSQLSERVER_33085 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33085 (Database Engine error)
ms.assetid: c27b8d1d-668a-4ba8-8b61-25a5ebbc5485
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dedb991845b520f17137e00955f30c51ed2b868c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456263"
---
# <a name="mssqlserver_33085"></a>MSSQLSERVER_33085
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|33085|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_CRYPTOPROVE_METHOD_CANNOT_FOUND|  
|Texte du message|Une ou plusieurs méthodes restent introuvables dans la bibliothèque du fournisseur de services de chiffrement '%.*ls'.|  
  
## <a name="explanation"></a>Explication  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu utiliser le fournisseur de services de chiffrement répertorié dans le message d’erreur. Le fournisseur de services de chiffrement n'a pas pris en charge une méthode requise. L'état de l'erreur indique quelle méthode était introuvable.  
  
|State|Description|  
|---------|---------------|  
|1|SqlCryptInitializeProvider|  
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
  
