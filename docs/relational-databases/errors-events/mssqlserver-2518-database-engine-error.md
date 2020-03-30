---
title: MSSQLSERVER_2518 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca6a654894304197357cbe244be60f9b9a58f789
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68138512"
---
# <a name="mssqlserver_2518"></a>MSSQLSERVER_2518
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2518|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Texte du message|ID d'objet O_ID (objet « O_NAME ») : impossible de vérifier les colonnes calculées et les types définis par l'utilisateur pour cet objet, parce que le CLR (Common Language Runtime) est désactivé.|  
  
## <a name="explanation"></a>Explication  
Ce message présenté à titre d'information indique que le processeur de requêtes n'a pas pu fournir à DBCC un objet interne autorisant l'évaluation des colonnes calculées et des types définis par l'utilisateur CLR (Common Language Runtime). Ce problème est survenu parce que l'une des colonnes impliquait le CLR ; or ce dernier n'est pas activé. L'objet interne couvre toutes les colonnes. Par conséquent, l'impossibilité d'évaluer une seule colonne empêche la création de l'objet interne. Cela signifie qu'il sera impossible de vérifier si les colonnes calculées sont correctes ou de les utiliser lorsque DBCC vérifiera la cohérence entre les index et les tables de base.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Activez le CLR et exécutez de nouveau l'instruction DBCC.  
  
## <a name="see-also"></a>Voir aussi  
[Activation de l’intégration du CLR](~/relational-databases/clr-integration/clr-integration-enabling.md)  
  
