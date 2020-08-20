---
description: Problèmes liés aux articles
title: Problèmes liés aux articles | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.articleissues.f1
ms.assetid: bde57da2-dd47-412f-9df7-9224968b2448
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: b1fdefcb9a356f17032338b5d4ba04bfc1ff37d1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482472"
---
# <a name="article-issues"></a>Problèmes liés aux articles
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  La page **Problèmes d'article** reprend les conditions déterminées relatives aux articles et à toute modification nécessaire découlant de ces conditions. Le tableau suivant répertorie les problèmes potentiels et les actions nécessaires pour vous assurer que la réplication et les applications existantes fonctionnent correctement.  
  
|Problème d'article|Détails|Action requise|  
|-------------------|-------------|---------------------|  
|Les colonnes Uniqueidentifier seront ajoutées aux tables|La réplication requiert une colonne de type de données **uniqueidentifier** correspondant à tous les articles d'une publication de fusion ou transactionnelle autorisant les abonnements de mise à jour.|La réplication ajoute automatiquement une colonne de type de données **uniqueidentifier** aux tables publiées qui n'en possèdent pas lors de la génération du premier instantané. Assurez-vous que les instructions INSERT et UPDATE appelant ces tables utilisent bien des listes de colonnes. Vérifiez également que l'espace disque est suffisant pour autoriser l'ajout de cette colonne.|  
|Les colonnes IDENTITY nécessitent l'option NOT FOR REPLICATION.|La réplication nécessite que toutes les colonnes IDENTITY utilisent l'option NOT FOR REPLICATION. Si une colonne IDENTITY publiée n'utilise pas cette option, les commandes INSERT risquent de ne pas se répliquer correctement.|S’applique aux publications créées sur des serveurs de publication exécutant [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ou version antérieure. Vous devez indiquer la propriété NOT FOR REPLICATION pour toutes les colonnes IDENTITY.|  
|La propriété IDENTITY n'est pas transférée aux abonnés.|Cette publication ne permet pas de mise à jour sur les Abonnés. Lorsque les colonnes IDENTITY sont transmises à l'Abonné, la propriété IDENTITY ne l'est cependant pas. Par exemple, une colonne définie en tant que INT IDENTITY sur le serveur de publication est définie en tant que INT sur l'Abonné.|S'applique aux publications créées sur des serveurs de publication exécutant [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ou antérieur. Aucune action n'est nécessaire.|  
|Des tables référencées par des vues sont nécessaires.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessite que toutes les tables référencées par des vues publiées, indexées ou non, soient disponibles dans l’Abonné. Si les tables référencées ne sont pas publiées en tant qu'articles dans cette publication, elles doivent être créées manuellement sur l'abonné.|Utilisez le bouton **Précédent** pour vous rendre à la page **Articles** . Ajoutez ensuite tout objet nécessaire.|  
|Des objets référencés par des procédures stockées sont nécessaires.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impose que tous les objets référencés par des procédures stockées publiées, tels que des tables et des fonctions définies par l'utilisateur soient disponibles pour l'Abonné. Si les objets référencés ne sont pas publiés en tant qu'articles dans cette publication, ils doivent être créés manuellement sur l'abonné.|Utilisez le bouton **Précédent** pour vous rendre à la page **Articles** . Ajoutez ensuite tout objet nécessaire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Créer une publication](../../relational-databases/replication/publish/create-a-publication.md)  
  
  
