---
title: Programmes de résolution COM Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: a6637e4b-4e6b-40aa-bee6-39d98cc507c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8fb5a27e9087044b1049106ca5abd071db74af9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63240212"
---
# <a name="microsoft-com-based-resolvers"></a>Microsoft COM-Based Resolvers
  Tous les programmes de résolution COM fournis avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gèrent les conflits de mise à jour, et lorsque cela est indiqué, ils gèrent également les conflits d'insertion et de suppression. Ils gèrent tous le suivi des colonnes et la plupart gèrent également le suivi des lignes. Ces programmes de résolution ainsi que tous les programmes de résolution COM déclarent les types de conflit qu'ils peuvent gérer. Ainsi, l'Agent de fusion utilise le programme de résolution par défaut pour tous les autres types de conflit.  
  
 Les programmes de résolution sont installés au cours du processus d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Exécutez la procédure stockée **sp_enumcustomresolvers** pour consulter tous les programmes de résolution de conflits inscrits sur un ordinateur. L'exécution de la procédure permet d'afficher la description et l'identificateur global unique (GUID) de chaque programme de résolution dans un ensemble de résultats séparé.  
  
 Pour spécifier un programme de résolution, consultez [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).  
  
 Le tableau suivant décrit les attributs des programmes de résolution spécifiques.  
  
|Name|Entrée requise|Description|Commentaires|  
|----------|--------------------|-----------------|--------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Outil de résolution des conflits additif|Nom de la colonne à totaliser. Elle doit être d'un type de données arithmétique (tel que **int**, **smallint**, **numeric**, etc.).|Le gagnant du conflit est déterminé à partir de la valeur de priorité. Les valeurs des colonnes spécifiées prennent la valeur représentant la somme des valeurs des colonnes source et de destination. Si l'une des colonnes a la valeur NULL, elles ont la valeur de l'autre colonne.|Prend uniquement en charge les conflits de mise à jour, le suivi de colonnes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Outil de résolution des conflits de moyenne|Nom de la colonne dont la moyenne doit être établie. Elle doit être d'un type de données arithmétique (tel que **int**, **smallint**, **numeric**, etc.).|Le gagnant du conflit est déterminé à partir de la valeur de priorité. Les valeurs de colonnes résultantes représentent la moyenne des valeurs des colonnes source et de destination. Si l'une des colonnes a la valeur NULL, elles ont la valeur de l'autre colonne.|Prend uniquement en charge les conflits de mise à jour, le suivi de colonnes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Outil de résolution des conflits DateTime (le plus ancien gagne)|Nom de la colonne à utiliser pour déterminer le gagnant du conflit. Elle doit posséder un type de données **datetime** .|La colonne dont la valeur **datetime** est la plus antérieure détermine le vainqueur du conflit. Si l'une des colonnes a la valeur NULL, la ligne contenant l’autre constitue le gagnant.|Prend en charge les conflits de mise à jour, le suivi de lignes et de colonnes. Les valeurs de colonne sont comparées directement, et aucun ajustement n'est réalisé pour les différents fuseaux horaires.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Outil de résolution des conflits DateTime (le plus récent gagne)|Nom de la colonne à utiliser pour déterminer le gagnant du conflit. Elle doit posséder un type de données **datetime** .|La colonne dont la valeur **datetime** est la plus récente détermine le vainqueur du conflit. Si l'une des colonnes a la valeur NULL, la ligne contenant l’autre constitue le gagnant.|Prend en charge les conflits de mise à jour, le suivi de lignes et de colonnes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Résolveur de conflits maximal|Nom de la colonne à utiliser pour déterminer le gagnant du conflit. Elle doit être d'un type de données arithmétique (tel que **int**, **smallint**, **numeric**, etc.).|La colonne dont la valeur numérique est la plus importante détermine le vainqueur du conflit. Si l'une des colonnes a la valeur NULL, la ligne contenant l’autre constitue le gagnant.|Prend en charge le suivi des lignes et des colonnes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Résolveur de conflit minimal|Nom de la colonne à utiliser pour déterminer le gagnant du conflit. Elle doit être d'un type de données arithmétique (tel que **int**, **smallint**, **numeric**, etc.).|La colonne dont la valeur numérique est la plus faible détermine le vainqueur du conflit. Si l'une des colonnes a la valeur NULL, la ligne contenant l’autre constitue le gagnant.|Prend en charge les conflits de mise à jour, le suivi de lignes et de colonnes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Outil de résolution des conflits de fusion de texte|Nom de la colonne de texte et délimiteur, par exemple `@resolver_info = '[col1][===]'`.|Le gagnant du conflit est déterminé à partir de la valeur de priorité. Les colonnes de texte en conflit prennent la valeur fusionnée, composée du préfixe commun suivi de la partie unique du serveur de publication, puis du délimiteur et enfin de la partie unique de l'Abonné.|Prend uniquement en charge les conflits de mise à jour, le suivi de colonnes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Programme de résolution des conflits de l’abonné Always WINS|Pas d'entrées.|L'abonné, qu'il soit la source ou la destination, est le vainqueur.|Prend en charge tous les types de conflits.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Résolveur de colonne de priorité|Nom de la colonne à utiliser pour déterminer le gagnant du conflit. Elle doit être d'un type de données arithmétique (tel que **int**, **smallint**, **numeric**, etc.).|La colonne dont la valeur numérique est la plus importante détermine le vainqueur du conflit. Si l'une des colonnes a la valeur NULL, la ligne contenant l’autre constitue le gagnant.|Prend en charge les conflits de mise à jour, le suivi de lignes et de colonnes.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Télécharger uniquement le programme de résolution des conflits|Pas d'entrées.|Les modifications téléchargées sur le serveur de publication sont acceptées mais les modifications ne sont pas téléchargées vers l'Abonné.|Prend en charge tous les types de conflits.|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Télécharger uniquement le programme de résolution des conflits|Pas d'entrées.|Les modifications téléchargées sur le serveur de publication sont rejetées mais les modifications sont téléchargées vers l'Abonné.|Prend en charge tous les types de conflits.|  
|Programme de résolution des procédures stockées[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQL Server|Nom de la procédure stockée que le programme de résolution doit appeler pour gérer le conflit.|La résolution du conflit dépend de la logique de la procédure stockée spécifiée.|Prend en charge les conflits de mise à jour. Pour plus d’informations, consultez [implémenter un outil personnalisé de résolution des conflits pour un article de fusion](../implement-a-custom-conflict-resolver-for-a-merge-article.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Détection et résolution avancées des conflits de réplication de fusion](advanced-merge-replication-conflict-detection-and-resolution.md)   
 [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql)  
  
  
