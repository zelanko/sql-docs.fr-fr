---
title: Générer des filtres | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14ccac181a4b76f8fc0423d6e00b20f91f8ea9cc
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67581361"
---
# <a name="generate-filters"></a>Générer des filtres
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La boîte de dialogue **Générer des filtres** permet de définir un filtre de lignes à appliquer sur une table lors d'une opération de publication de fusion. La réplication étend ensuite automatiquement le filtre aux autres tables associées par le biais de relations de clé étrangère. Par exemple, si vous définissez un filtre portant sur une table contenant des données de clients pour ne garder que les données portant sur les clients français, la réplication étend donc ce filtre aux tables retraçant les informations propres aux commandes et à leurs détails en relation avec des clients français.  
  
## <a name="options"></a>Options  
 Cette boîte de dialogue permet d'initier un processus en trois étapes afin de créer un filtre de lignes portant sur une table. Le filtre ainsi créé est ensuite étendu aux tables possédant une relation à la table filtrée à travers leur clé primaire et leurs relations de clé étrangère. Prenons pour exemple trois tables nommées **Customer**, **SalesOrderHeader**et **SalesOrderDetail**. Les tables **Customer** et **SalesOrderHeader**possèdent une relation entre elles et une autre existe entre **SalesOrderHeader** et **SalesOrderDetail**. Si nous appliquons un filtre de lignes à **Customer**, la réplication étend ainsi ce filtre à **SalesOrderHeader** et à **SalesOrderDetail**.  
  
1.  **Sélectionnez la table à filtrer.**  
  
     Sélectionnez une table dans la zone de liste déroulante. Les tables n'y apparaissent que si elles ont été sélectionnées dans la page **Articles** .  
  
2.  **Complétez l'instruction de filtrage pour identifier les lignes de table que les abonnés doivent recevoir.**  
  
     Définissez une nouvelle instruction de filtrage. La zone de liste déroulante **Colonnes** répertorie toutes les colonnes que vous publiez à partir de la table à choisir dans **Sélectionnez la table à filtrer**. La zone de texte **Instruction de filtrage** comprend un texte par défaut, qui est de la forme suivante :  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     Ce texte ne peut pas être modifié. Saisissez dans ce cas la clause de filtrage après le mot clé WHERE en suivant la syntaxe standard [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
    > [!IMPORTANT]  
    >  Pour des raisons de performances, il est recommandé de ne pas appliquer de fonctions aux noms de colonnes dans les clauses de filtres de lignes paramétrables, comme `LEFT([MyColumn]) = SUSER_SNAME()`. Si vous utilisez HOST_NAME dans une clause de filtrage puis en remplacez la valeur, il peut s'avérer judicieux de convertir les types de données avec la fonction CONVERT. Pour plus d'informations sur la conduite à adopter dans cette situation, consultez la section « Substitution de la valeur de HOST_NAME » de la rubrique [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
3.  **Spécifiez combien d'abonnements recevront des données de cette table.**  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only. Merge replication allows you to specify the type of partitions that are best suited to your data and application. If you select **A row from this table will go to only one subscription**, merge replication sets the nonoverlapping partitions option. Nonoverlapping partitions work in conjunction with precomputed partitions to improve performance, with nonoverlapping partitions minimizing the upload cost associated with precomputed partitions. The performance benefit of nonoverlapping partitions is more noticeable when the parameterized filters and join filters used are more complex. If you select this option, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber. For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
 Après avoir ajouté un filtre, cliquez sur **OK** pour quitter ainsi la boîte de dialogue. Le filtre que vous spécifiez est ensuite analysé et exécuté sur la table indiquée dans la clause SELECT. Si l'instruction de filtrage contient des erreurs de syntaxe ou d'autres erreurs, vous recevrez un message et pourrez modifier l'instruction de filtrage.  
  
 Après l'analyse de l'instruction, la réplication procède à la création des filtres de jointure nécessaires. Si vous n'avez pas encore configuré le serveur de distribution pour le serveur de publication pour lequel cet Assistant est censé s'exécuter, un message vous invite alors à le configurer.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtrer des données publiées](../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtres de jointure](../../relational-databases/replication/merge/join-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
