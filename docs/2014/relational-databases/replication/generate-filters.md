---
title: Générer des filtres | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cae79be898c326b395e781db741c87578edfe7ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721280"
---
# <a name="generate-filters"></a>Générer des filtres
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
    >  Pour des raisons de performances, il est recommandé de ne pas appliquer de fonctions aux noms de colonnes dans les clauses de filtres de lignes paramétrables, comme `LEFT([MyColumn]) = SUSER_SNAME()`. Si vous utilisez HOST_NAME dans une clause de filtrage puis en remplacez la valeur, il peut s'avérer judicieux de convertir les types de données avec la fonction CONVERT. Pour plus d'informations sur la conduite à adopter dans cette situation, consultez la section « Substitution de la valeur de HOST_NAME » de la rubrique [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
3.  **Spécifiez combien d'abonnements recevront des données de cette table.**  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. La réplication de fusion vous permet d'indiquer le type de partitions répondant au mieux à vos données et votre application. Si vous sélectionnez **Une ligne de cette table ira à un seul abonnement**, la réplication de fusion définit l'option de non-chevauchement des partitions. Cette option, qui fonctionne avec les partitions précalculées pour améliorer les performances, permet de réduire au minimum le coût de téléchargement associé aux partitions précalculées. Le gain de performances lié au non-chevauchement des partitions est plus flagrant lorsque les filtres paramétrés et les filtres de jointure utilisés sont plus complexes. Si vous sélectionnez cette option, vous devez veiller à ce que les données soient partitionnées de telle sorte qu'une ligne ne puisse pas être répliquée vers plusieurs abonnés. Pour plus d'informations, consultez la section « Définition de « partition options » » dans la rubrique [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
 Après avoir ajouté un filtre, cliquez sur **OK** pour quitter ainsi la boîte de dialogue. Le filtre que vous spécifiez est ensuite analysé et exécuté sur la table indiquée dans la clause SELECT. Si l'instruction de filtrage contient des erreurs de syntaxe ou d'autres erreurs, vous recevrez un message et pourrez modifier l'instruction de filtrage.  
  
 Après l'analyse de l'instruction, la réplication procède à la création des filtres de jointure nécessaires. Si vous n'avez pas encore configuré le serveur de distribution pour le serveur de publication pour lequel cet Assistant est censé s'exécuter, un message vous invite alors à le configurer.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)   
 [Filtrer des données publiées](publish/filter-published-data.md)   
 [Filtres de jointure](merge/join-filters.md)   
 [Filtres de lignes paramétrés](merge/parameterized-filters-parameterized-row-filters.md)   
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)  
  
  
