---
title: "MSSQLSERVER_825 | Microsoft Docs"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6cf3cceebd5555e91d3753e385d28164680241f5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver825"></a>MSSQLSERVER_825
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|825|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|B_RETRYWORKED|  
|Texte du message|La lecture du fichier '%ls' au décalage %#016I64x a réussi après avoir échoué %d fois avec l'erreur %ls. D'autres messages peuvent fournir davantage d'informations dans le journal des erreurs SQL Server et le journal des événements système. Cette condition d'erreur menace l'intégrité de la base de données et elle doit être résolue. Effectuez une vérification complète de la cohérence de la base de données (DBCC CHECKDB). Cette erreur peut avoir de nombreuses causes ; pour plus d'informations, consultez la documentation en ligne de SQL Server.|  
  
## <a name="explanation"></a>Explication  
Ce message indique que l'opération de lecture a dû être réexécutée au moins une fois et signale un problème majeur avec le lecteur de disques. Ce message n'indique pas pour le moment un problème avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais le problème de disque peut entraîner la perte de données ou l'altération de bases de données s'il n'est pas résolu. Le journal des événements système peut contenir des événements associés qui vous aideront à diagnostiquer le problème. Pour plus d’informations sur les erreurs d’E/S, consultez [Concepts de base des E/S Microsoft SQL Server, chapitre 2](http://go.microsoft.com/fwlink/?LinkId=69370).  
  
## <a name="user-action"></a>Action de l'utilisateur  
Les actions suivantes peuvent vous aider à identifier et à résoudre le problème sous-jacent :  
  
-   Consultez le journal des erreurs et le texte spécifique de ce message pour trouver des indications expliquant pourquoi le problème s'est produit.  
  
-   Vérifiez votre système de disques. Le problème peut être lié aux disques, aux contrôleurs de disques, aux cartes de disques ou aux pilotes de disques.  
  
-   Contactez le fabricant de vos disques pour vous procurer les utilitaires les plus récents afin de vérifier l'état de votre système de disques.  
  
-   Contactez le fabricant de vos disques pour obtenir les dernières mises à jour des pilotes.  
  

