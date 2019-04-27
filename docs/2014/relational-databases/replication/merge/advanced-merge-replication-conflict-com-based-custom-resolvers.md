---
title: Programmes de résolution personnalisés COM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 27d5be264fc6e6033997babb4a7aac1e8271a39d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63066307"
---
# <a name="com-based-custom-resolvers"></a>COM-Based Custom Resolvers
  Les programmes de résolution personnalisés offrent une plus grande souplesse que le mécanisme de résolution par défaut et ils peuvent implémenter la logique métier requise par les applications utilisant les données répliquées. Un programme de résolution personnalisé COM est une bibliothèque de liens dynamiques (DLL) qui implémente l'interface **ICustomResolver** , ses méthodes et ses propriétés, ainsi que d'autres interfaces de prise en charge et définitions de types conçues spécifiquement pour la résolution de conflits.  
  
> [!NOTE]  
>  Il est recommandé d'utiliser si possible un gestionnaire de logique métier au lieu d'un programme de résolution personnalisé COM. Pour plus d’informations sur les gestionnaires de logique métier, consultez [Exécuter la logique métier lors de la synchronisation de fusion](execute-business-logic-during-merge-synchronization.md).  
  
 Pour créer un programme de résolution personnalisé COM, vous pouvez utiliser la bibliothèque de types fournie dans le fichier replrec.dll. Cette bibliothèque est installée par défaut dans [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.  
  
 Avant d'écrire un programme de résolution personnalisé COM, vous devez décider des éléments suivants :  
  
-   Types des modifications de ligne à résoudre, tels que les mises à jour, insertions et suppressions ainsi que l'appel ou non du programme de résolution au cours du chargement des modifications de fusion, leur téléchargement, ou les deux. Vous pouvez spécifier un type de modification, toutes les modifications ou n'importe quelle combinaison. Le programme de résolution de conflits de fusion par défaut gère tous les conflits non pris en charge par un programme de résolution personnalisé.  
  
-   Utilisation du suivi des colonnes lors de la résolution du conflit. Lorsque le suivi au niveau des colonnes est activé, seules les données des colonnes présentant un conflit sont signalées en tant que tel, dans le cas contraire, les données sont fusionnées. Cependant, les conflits sont résolus de la même façon qu'avec le suivi au niveau des lignes : la ligne prioritaire remplace toute la ligne de données (mais ces données peuvent être un mélange entre les valeurs du serveur de publication, des Abonnés, ou certaines valeurs modifiées qui n'appartiennent ni au serveur de publication ni aux Abonnés). Pour plus d’informations, consulter [Détecter et résoudre des conflits de réplication de fusion](advanced-merge-replication-conflict-detection-and-resolution.md).  
  
 Pour implémenter un outil de résolution des conflits personnalisé COM, consultez [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](../implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
 Un programme de résolution personnalisé est spécifié pour un article mais pas pour l'intégralité d'une publication. Le même programme de résolution peut être spécifié avec plusieurs articles mais la logique des programmes de résolution personnalisés est souvent propre à une table donnée. Si la table utilisée dans l'article est modifiée après la création d'un programme de résolution (par exemple, attribution d'un nouveau nom à une colonne intervenant dans la résolution du conflit), il se peut que le programme de résolution personnalisé doive être modifié et recompilé.  
  
 Pour spécifier un programme de résolution personnalisé, consultez [Spécifier un programme de résolution d'articles de fusion](../publish/specify-a-merge-article-resolver.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Détection et résolution des conflits de réplication de fusion avancée](advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Microsoft-programmes de résolution COM](advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
