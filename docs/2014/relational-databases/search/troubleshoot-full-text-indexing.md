---
title: Résoudre l’indexation de texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- indexes [full-text search]
- troubleshooting [SQL Server], full-text search
- troubleshooting [full-text search]
ms.assetid: 964c43a8-5019-4179-82aa-63cd0ef592ef
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 33fe6bd04e59f91588f651877295ea265d523635
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200369"
---
# <a name="troubleshoot-full-text-indexing"></a>Résoudre l’indexation de texte intégral
     
##  <a name="failure"></a> Dépanner les échecs de l'indexation de texte intégral  
 Lors du remplissage ou de la gestion d'un index de recherche en texte intégral, il est possible que l'indexeur de texte intégral, pour les raisons détaillées ci-dessous, ne parvienne pas à indexer une ou plusieurs lignes. Ces erreurs au niveau des lignes n'empêchent pas l'achèvement du remplissage. L'indexeur ignore ces lignes, et leur contenu ne peut donc pas être interrogé.  
  
 Les défaillances d'indexation peuvent se produire dans les cas suivants :  
  
-   L'indexeur ne peut pas trouver ou charger un composant de filtre ou d'analyseurs lexicaux. Ce problème peut se produire si la ligne de la table contient un format de document ou un contenu dans une langue qui n'a pas été inscrite avec l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il peut également se produire si le composant inscrit de l'analyseur lexical ou du filtre n'est pas signé, ou en cas d'échec de la vérification de la signature lors de son chargement.  
  
-   Un composant, par exemple un analyseur lexical ou un filtre, échoue et renvoie une erreur à l'indexeur. Cette situation peut se produire si le document en cours d'indexation est endommagé, interdisant au filtre d'extraire le texte du document. Elle peut également survenir lorsqu'un composant est incapable de traiter le contenu d'une même ligne au-delà d'une certaine taille, en raison de limitations de mémoire sur l'hôte de démon de filtre de texte intégral (fdhost.exe).  
  
 Pour chaque défaillance au niveau d'une ligne, le journal de l'analyse contient des détails sur les raisons qui l'ont provoquée. Le nombre d'erreurs est résumé à la fin d'un remplissage complet ou incrémentiel.  
  
 D'autres défaillances peuvent avoir un effet sur le processus d'indexation lui-même et empêcher l'achèvement du remplissage :  
  
-   L'index de texte intégral dépasse le nombre maximal de lignes admissibles dans un catalogue de texte intégral.  
  
-   Un index cluster ou un index clé de texte intégral sur la table en cours d'indexation est modifié, supprimé ou reconstruit.  
  
-   Une défaillance matérielle ou l'endommagement d'un disque provoque l'endommagement du catalogue de texte intégral.  
  
-   Un groupe de fichiers contenant la table en cours d'indexation de texte intégral est mis hors ligne ou en lecture seule.  
  
 Il convient de consulter le journal d'analyse à la fin de toutes les opérations lourdes de remplissage d'index de texte intégral ou lorsqu'un remplissage ne s'est pas achevé.  
  
### <a name="unsigned-components"></a>Composants non signés  
 Par défaut, l'indexeur de texte intégral requiert que les filtres et les analyseurs lexicaux qu'il charge soient signés. S'ils ne sont pas signés, ce qui arrive parfois lorsque des composants personnalisés sont installés, vous devez configurer l'indexeur de texte intégral pour qu'il ignore la vérification de signature.  
  
> [!IMPORTANT]  
>  Le fait d'ignorer la vérification de signature réduit la sécurité de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il est recommandé de signer tous les composants que vous implémentez ou de vérifier que tous les composants que vous achetez sont signés. Pour plus d’informations sur la signature des composants, consultez [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).  
  

  
##  <a name="state"></a> Index de recherche en texte intégral dans un état non cohérent une fois le journal des transactions restauré  
 Lors de la restauration du journal des transactions d'une base de données, il arrive qu'un message d'avertissement s'affiche en indiquant que l'index de recherche en texte intégral n'est pas dans un état cohérent. Cela se produit lorsque l'index de recherche en texte intégral d'une table est modifié après la sauvegarde de la base de données. Pour rendre un état cohérent à l'index de recherche en texte intégral, vous devez exécuter un remplissage complet (analyse) sur la table. Pour plus d’informations, consultez [Alimenter des index de recherche en texte intégral](../indexes/indexes.md).  
  

  
## <a name="see-also"></a>Voir aussi  
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)   
 [Alimenter des index de recherche en texte intégral](../indexes/indexes.md)  
  
  
