---
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9cf2edc55900ceb2181d5ae0d300300376f3ecbe
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553484"
---
# <a name="mssqlserver_1807"></a>MSSQLSERVER_1807
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1807|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|CANNOT_EX_LOCK|  
|Texte du message|Impossible d'obtenir un verrou exclusif sur la base de données '%.*ls'. Recommencez l'opération ultérieurement.|  
  
## <a name="explanation"></a>Explication  
 Une opération qui requérait un accès exclusif à la base de données n'a pas pu l'obtenir.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Arrêtez toutes les connexions à cette base de données ou relancez la requête ultérieurement.  
  
  
