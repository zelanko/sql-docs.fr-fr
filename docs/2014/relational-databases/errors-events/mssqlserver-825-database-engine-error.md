---
title: MSSQLSERVER_825 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c64c667fda282d6693af04c92a92f7d52e4cc9e4
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553188"
---
# <a name="mssqlserver_825"></a>MSSQLSERVER_825
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|825|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|B_RETRYWORKED|  
|Texte du message|La lecture du fichier '%ls' au décalage %#016I64x a réussi après avoir échoué %d fois avec l'erreur %ls. D'autres messages peuvent fournir davantage d'informations dans le journal des erreurs SQL Server et le journal des événements système. Cette condition d'erreur menace l'intégrité de la base de données et elle doit être résolue. Effectuez une vérification complète de la cohérence de la base de données (DBCC CHECKDB). Cette erreur peut avoir de nombreuses causes ; pour plus d'informations, consultez la documentation en ligne de SQL Server.|  
  
## <a name="explanation"></a>Explication  
 Ce message indique que l'opération de lecture a dû être réexécutée au moins une fois et signale un problème majeur avec le lecteur de disques. Ce message n'indique pas pour le moment un problème avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais le problème de disque peut entraîner la perte de données ou l'altération de bases de données s'il n'est pas résolu. Le journal des événements système peut contenir des événements associés qui vous aideront à diagnostiquer le problème. Pour plus d’informations sur les erreurs d’E/S, consultez [Concepts de base des E/S Microsoft SQL Server, chapitre 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Les actions suivantes peuvent vous aider à identifier et à résoudre le problème sous-jacent :  
  
-   Consultez le journal des erreurs et le texte spécifique de ce message pour trouver des indications expliquant pourquoi le problème s'est produit.  
  
-   Vérifiez votre système de disques. Le problème peut être lié aux disques, aux contrôleurs de disques, aux cartes de disques ou aux pilotes de disques.  
  
-   Contactez le fabricant de vos disques pour vous procurer les utilitaires les plus récents afin de vérifier l'état de votre système de disques.  
  
-   Contactez le fabricant de vos disques pour obtenir les dernières mises à jour des pilotes.  
  
  
