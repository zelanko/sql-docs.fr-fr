---
title: Utiliser l’Assistant Indexation de texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextindexingwizard.selecttablecolumns.f1
- sql12.swb.fulltextindexingwizard.welcome.f1
- sql12.swb.fulltextindexingwizard.selectacatalog.f1
- sql12.swb.fulltextindexingwizard.progress.f1
- sql12.swb.fulltextindexingwizard.selectorcreatepopschedules.f1
- sql12.swb.fulltextindexingwizard.selectatableorview.f1
- sql12.swb.fulltextindexingwizard.selectchangetracking.f1
- sql12.swb.fulltextindexingwizard.selectanindex.f1
- sql12.swb.fulltextindexingwizard.summary.f1
helpviewer_keywords:
- Full-Text Indexing Wizard
- full-text search [SQL Server], Full-Text Indexing Wizard
ms.assetid: 3e9d9605-6525-4781-9168-fdaa06db3459
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fea70d6b1230b67b2eedcdf1c7d2e82d2324a0b3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85016319"
---
# <a name="use-the-full-text-indexing-wizard"></a>Utiliser l'Assistant Indexation de texte intégral
  L'Assistant Indexation de texte intégral vous guide tout au long d'une série d'étapes destinées à vous aider à créer un index de texte intégral.  
  
#### <a name="to-use-the-full-text-indexing-wizard"></a>Pour utiliser l'Assistant Indexation de texte intégral  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur la table sur laquelle vous souhaitez créer un index de recherche en texte intégral, pointez sur **Index de recherche en texte intégral**, puis cliquez sur **Define Full-Text Index**(Définir l’index de recherche en texte intégral).  
  
     **Index unique**  
     Sélectionnez un index dans la liste déroulante. Cet index doit être un index unique, n'acceptant pas les valeurs Null, avec une colonne à clé unique. Sélectionnez le plus petit index de clé unique comme clé unique de texte intégral. Pour optimiser les performances, un index cluster est recommandé.  
  
     **Colonnes disponibles**  
     Pour inclure une colonne dans l'index, activez la case à cocher en regard du nom de la colonne. Les colonnes sur lesquelles ne doivent pas porter l'indexation de texte intégral sont grisées et leur case à cocher est désactivée.  
  
     **Langue pour l'analyseur lexical**  
     Sélectionnez une langue dans la liste déroulante. Ce choix sera utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour identifier les analyseurs lexicaux appropriés pour l'index. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des analyseurs lexicaux pour identifier les limites des mots dans les données indexées en texte intégral.  
  
     **Colonne de type**  
     Sélectionnez le nom de la colonne qui contient le type de document de la colonne indexée en texte intégral.  
  
     La **colonne de type** est activée uniquement lorsque la colonne nommée dans la colonne **colonnes disponibles** est de `varbinary(max)` type `image` ou.  
  
     **Sémantique statistique**  
     Sélectionnez s'il faut activer l'indexation sémantique pour la colonne sélectionnée. Pour plus d’informations, consultez [Recherche sémantique &#40;SQL Server&#41;](semantic-search-sql-server.md).  
  
     Si vous sélectionnez une **langue** avant de sélectionner **Sémantique statistique**, et que la langue sélectionnée n'est pas associée à un modèle linguistique sémantique, la case à cocher **Sémantique statistique** est désactivée. Si vous sélectionnez **Sémantique statistique** avant de sélectionner une **langue**, les langues disponibles dans la zone de liste déroulante sont limitées à celles pour lesquelles il existe une prise en charge de modèle linguistique sémantique.  
  
2.  Sélectionnez les options de suivi des modifications.  
  
     **Automatiquement**  
     Activez cette case d'option pour que l'index de texte intégral soit mis à jour automatiquement lorsque des modifications sont apportées aux données sous-jacentes.  
  
     **Manuellement**  
     Activez cette case d'option si vous ne voulez pas que l'index de texte intégral soit mis à jour automatiquement lorsque des modifications sont apportées aux données sous-jacentes. Les modifications apportées aux données sous-jacentes sont conservées. Toutefois, pour appliquer les modifications à l'index de texte intégral, vous devez démarrer ou planifier ce processus manuellement.  
  
     **Aucun suivi**  
     Activez cette case d'option si vous ne voulez pas que l'index de texte intégral soit mis à jour avec les modifications apportées aux données sous-jacentes.  
  
     **Démarrer le remplissage complet une fois l'index créé**  
     Activez cette case d'option pour déclencher un remplissage complet lorsque cet Assistant se détermine avec succès. Cela consiste à créer la structure d'index de texte intégral dans le catalogue et à la remplir avec les données indexées en texte intégral.  
  
3.  Sélectionnez le catalogue, le groupe de fichiers de l'index et la liste de mots vides.  
  
     **Sélectionner un catalogue de recherche en texte intégral**  
     Sélectionnez un catalogue de texte intégral dans la liste. Le catalogue par défaut pour la base de données devient l'élément sélectionné par défaut dans la liste. Si aucun catalogue n’est disponible, cette dernière est désactivée, et la case **Créer un nouveau catalogue** est cochée, mais désactivée.  
  
    |||  
    |-|-|  
    |**Créer un catalogue**|Sélectionnez cette option pour créer un nouveau catalogue de texte intégral.|  
  
     **Nom**  
     Entrez le nom du nouveau catalogue de texte intégral.  
  
     **Définir en tant que catalogue par défaut**  
     Sélectionnez cette option afin que le catalogue devienne la valeur par défaut pour cette base de données.  
  
     **Respect des accents**  
     Indiquez si le nouveau catalogue doit respecter les accents ou non. Si la base de données respecte les accents, l’option **Respect** est sélectionnée par défaut.  
  
     **Sélectionner le groupe de fichiers d'index**  
     Spécifiez le groupe de fichiers sur lequel créer l'index de recherche en texte intégral.  
  
     Sélectionnez l'une des valeurs suivantes :  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |**\<default>**|Si la table ou la vue n'est pas partitionnée, sélectionnez cette option pour utiliser le même groupe de fichiers que la table ou la vue sous-jacente. Si la table ou la vue est partitionnée, le groupe de fichiers primaire est utilisé.|  
    |**ESSENTIELLES**|Sélectionnez cette option pour utiliser le groupe de fichiers primaire pour le nouvel index de recherche en texte intégral.|  
    |*groupe de fichiers par défaut spécifié par l’utilisateur*|S'il existe une liste de mots vides par défaut définie par l'utilisateur, sélectionnez son nom dans la liste pour utiliser ce groupe de fichiers pour le nouvel index de recherche en texte intégral.|  
  
     **Sélectionner la liste de mots vides de texte intégral**  
     Spécifiez une liste de mots vides à utiliser pour l'index de recherche en texte intégral ou désactivez l'utilisation de listes de mots vides.  
  
     Dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures, les mots vides sont gérés dans les bases de données à l'aide d'objets appelés listes de mots vides. Une *liste de mots vides* est une liste qui, associée à un index de recherche en texte intégral, s’applique aux requêtes de texte intégral sur cet index. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
     Sélectionnez l'une des valeurs suivantes :  
  
    |Valeur|Description|  
    |-----------|-----------------|  
    |**\<system>**|Sélectionnez cette option pour utiliser la liste de mots vides système sur le nouvel index de recherche en texte intégral. Il s'agit du paramètre par défaut.|  
    |**\<off>**|Sélectionnez cette option pour désactiver des listes de mots vides pour le nouvel index de recherche en texte intégral.|  
    |*user-defined-stoplist-name*|La liste affiche le nom de chaque liste de mots vides définie par l'utilisateur, le cas échéant, qui a été créée sur la base de données. Sélectionnez une liste de mots vides définie par l'utilisateur à utiliser pour le nouvel index de recherche en texte intégral.|  
  
4.  Éventuellement, vous pouvez définir la planification de remplissage. Les opérations d'indexation commencent alors immédiatement, sauf si elles ont été planifiées pour plus tard. Les planifications sont créées immédiatement, même si elles ne seront pas exécutées avant l'heure planifiée.  
  
     **Nouvelle planification de table**  
     Définition d'un remplissage de planification de table.  
  
     **Nouvelle planification de catalogue**  
     Définition d'un remplissage de planification d'un catalogue de texte intégral.  
  
     **Modifier**  
     Modification d'une planification.  
  
     **Supprimer**  
     Suppression d'une planification.  
  
5.  Affichage ou contrôle de la progression de l'Assistant Indexation de texte intégral.  
  
     **Stop**  
     Interrompt l'opération en cours et empêche l'Assistant d'exécuter les opérations de texte intégral suivantes au cours de cette session.  
  
     **Report**  
     Lorsque toutes les opérations ont fini de s'exécuter, cliquez sur ce bouton pour accéder à un rapport sur les opérations effectuées. Vous pouvez afficher le rapport, l'imprimer dans un fichier, le copier dans le Presse-papiers ou l'envoyer par courrier électronique.  
  
  
