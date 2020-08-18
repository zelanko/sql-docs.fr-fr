---
description: MSSQLSERVER_15404
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a9a05c8e47e97357b562a3429b98fe856e60d75f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88333855"
---
# <a name="mssqlserver_15404"></a>MSSQLSERVER_15404
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|15404|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_NTGRP_ERROR|  
|Texte du message|Impossible d’obtenir des informations sur l’utilisateur ou le groupe ’*utilisateur*’, code d’erreur *code*.|  
  
## <a name="explanation"></a>Explication  
15404 est utilisé dans l'authentification lorsqu'un principal non valide est spécifié. Sinon, l'emprunt d'identité d'un compte Windows échoue car il n'existe aucune relation de confiance totale entre le compte de service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le domaine du compte Windows.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez que le principal Windows existe et qu'il est orthographié correctement.  
  
Si cette erreur est due à un échec d'une relation de confiance totale entre le compte de service de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le domaine du compte Windows, une des actions suivantes peut résoudre l'erreur :  
  
-   Utilisez un compte du même domaine que l'utilisateur Windows pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un compte d'ordinateur tel que Service réseau ou Système local, l'ordinateur doit être approuvé par le domaine contenant l'utilisateur Windows.  
  
-   Utilisez un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
