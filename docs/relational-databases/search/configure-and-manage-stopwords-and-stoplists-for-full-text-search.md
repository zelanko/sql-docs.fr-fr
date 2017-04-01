---
title: "Configurer et g&#233;rer les mots vides et listes de mots vides pour la recherche en texte int&#233;gral | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liste de mots vides [recherche en texte intégral]"
  - "recherche en texte intégral [SQL Server], liste de mots vides"
  - "recherche en texte intégral [SQL Server], mots parasites"
  - "mots parasites [recherche en texte intégral]"
  - "recherche en texte intégral [SQL Server], mots vides"
  - "mots vides [recherche en texte intégral]"
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
caps.latest.revision: 81
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 79
---
# Configurer et g&#233;rer les mots vides et listes de mots vides pour la recherche en texte int&#233;gral
  Pour éviter que l'index de recherche en texte intégral ne devienne encombré, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un mécanisme qui ignore les chaînes courantes qui ne sont d'aucune utilité pour la recherche. Ces chaînes ignorées sont appelées des *mots vides*. Pendant la création d'un index, le moteur de texte intégral omet les mots vides de l'index de recherche en texte intégral. Cela signifie que les requêtes de texte intégral ne rechercheront pas les mots vides.  
  
##  <a name="understand"></a> Présentation des mots vides et listes de mots vides  
 Un mot vide peut être un mot ayant une signification dans une langue spécifique ou être un *jeton* qui n’a pas de signification linguistique. Par exemple, en français, les mots tels que « un », « et », « est » ou « le » sont écartés de l'index de recherche en texte intégral, car ils sont inutiles dans le cadre d'une recherche.  
  
 Bien qu'il ignore l'inclusion des mots vides, l'index de recherche en texte intégral prend en considération leur position. Prenons l'exemple de l'expression suivante : « Instructions are applicable to these Adventure Works Cycles models ». Le tableau suivant décrit la position des mots dans l'expression :  
  
|Word|Position|  
|----------|--------------|  
|Instructions|1|  
|are|2|  
|applicable|3|  
|to|4|  
|these|5|  
|Adventure|6|  
|Works|7|  
|Cycles|8|  
|modèles|9|  
  
 Les mots vides « are », « to » et « these » situés aux positions 2, 4 et 5 sont écartés de l'index de recherche en texte intégral. Cependant, les informations relatives à leur position sont conservées, sans affecter la position des autres mots de l'expression.  
  
 Les mots vides sont gérés dans des bases de données à l'aide d'objets appelés des listes de mots vides. Une *liste de mots vides* est une liste qui, associée à un index de recherche en texte intégral, s’applique aux requêtes de texte intégral sur cet index.  
  
 [Dans cette rubrique](#TOP)  
  
##  <a name="creating"></a> Création d'une liste de mots vides  
 Vous pouvez créer une liste de mots vides de l'une des façons suivantes :  
  
-   Utilisation de la liste de mots vides fournie par le système dans la base de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fourni avec une liste de mots vides système qui contient les mots vides les plus couramment utilisés pour chaque langue prise en charge, c’est-à-dire pour chaque langue associée aux analyseurs lexicaux fournis par défaut. La liste de mots vides système contient les mots vides courants pour toutes les langues prises en charge.  Vous pouvez copier la liste de mots vides système, et personnaliser cette liste en ajoutant et en supprimant des mots vides.  
  
     La liste de mots vides système est installée dans la base de données [Resource](../../relational-databases/databases/resource-database.md).  
  
-   Créer votre propre liste de mots vides, puis en lui ajoutant des mots vides pour chaque langue que vous spécifiez. Vous pouvez également supprimer des mots vides de votre liste de mots vides si nécessaire.  
  
-   Télécharger une liste de mots vides personnalisée depuis toute autre base de données dans l'instance de serveur actuelle, puis ajouter et supprimer des mots vides au besoin.  
  
 **Pour créer une liste de mots vides**  
  
-   [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)  
  
#### Pour créer une liste de mots vides de texte intégral dans Management Studio  
  
1.  Dans l'Explorateur d'objets, développez le serveur.  
  
2.  Développez **Bases de données**, puis développez la base de données dans laquelle vous souhaitez créer la liste de mots vides de texte intégral.  
  
3.  Développez **Stockage**, puis cliquez avec le bouton droit sur **Listes de mots vides de texte intégral**.  
  
4.  Sélectionnez **Nouvelle liste de mots vides de texte intégral**.  
  
5.  Spécifiez le nom de la liste de mots vides.  
  
6.  Éventuellement, spécifiez une autre personne comme propriétaire de la liste de mots vides.  
  
7.  Sélectionnez l'une des options de création de liste de mots vides suivantes :  
  
    -   **Créer une liste de mots vides vide**  
  
    -   **Créer à partir de la liste de mots vides système**  
  
    -   **Créer à partir d'une liste de mots vides de texte intégral existante**  
  
     Pour plus d’informations, consultez [Nouvelle liste de mots vides de texte intégral &#40;page Général&#41;](../Topic/New%20Full-Text%20Stoplist%20\(General%20Page\).md).  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 **Pour supprimer une liste de mots vides**  
  
-   [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)  
  
 [Dans cette rubrique](#TOP)  
  
##  <a name="queries"></a> Utilisation d'une liste de mots vides dans les requêtes de texte intégral  
 Pour utiliser une liste de mots vides dans des requêtes, vous devez l'associer à un index de recherche en texte intégral. Vous pouvez joindre une liste de mots vides à un index de recherche en texte intégral lorsque vous créez l'index, ou vous pouvez modifier ultérieurement l'index pour ajouter une liste de mots vides.  
  
 **Pour créer un index de recherche en texte intégral et lui associer une liste de mots vides**  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)  
  
 **Pour associer ou dissocier une liste de mots vides avec un index de recherche en texte intégral existant**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
 **Pour supprimer un message d'erreur si des mots vides provoquent l'échec d'une opération booléenne sur une requête de texte intégral**  
  
-   [Transformer les mots parasites (option de configuration de serveur)](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)  
  
 [Dans cette rubrique](#TOP)  
  
##  <a name="viewing"></a> Consultation des listes de mots vides et des métadonnées de liste de mots vides  
 **Pour afficher tous les mots vides d'une liste de mots vides**  
  
-   [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
 **Pour obtenir des informations sur toutes les listes de mots vides dans la base de données actuelle**  
  
-   [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)  
  
-   [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
 **Pour consulter le résultat de la segmentation du texte en unités lexicales d'une combinaison d'analyseur lexical, de dictionnaire des synonymes et de liste de mots vides**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md)  
  
 [Dans cette rubrique](#TOP)  
  
##  <a name="change"></a> Modification des mots vides dans une liste de mots vides  
 **Pour ajouter ou supprimer des mots vides dans une liste de mots vides**  
  
-   [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)  
  
#### Pour modifier les mots vides dans une liste de mots vides dans Management Studio  
  
1.  Dans l'Explorateur d'objets, développez le serveur.  
  
2.  Développez **Bases de données**, puis développez la base de données.  
  
3.  Développez **Stockage**, puis sélectionnez **Listes de mots vides de texte intégral**.  
  
4.  Cliquez avec le bouton droit sur la liste de mots vides dont vous souhaitez modifier les propriétés, puis sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue [Propriétés de la liste de mots vides de texte intégral](../Topic/Full-Text%20Stoplist%20Properties.md) :  
  
    1.  Dans la zone de liste **Action**, sélectionnez l’une des actions suivantes : **Ajouter un mot vide**, **Supprimer le mot vide**, **Supprimer tous les mots vides** ou **Effacer la liste de mots vides**.  
  
    2.  Si la zone de texte **Mot vide** est activée pour l’action sélectionnée, entrez un mot vide unique. Ce nouveau mot vide doit être unique ; autrement dit, il ne doit pas déjà figurer dans la liste de mots vides correspondant à la langue sélectionnée.  
  
    3.  Si la zone de liste **Langue de texte intégral** est activée pour l’action sélectionnée, sélectionnez une langue.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 [Dans cette rubrique](#TOP)  
  
##  <a name="upgrade"></a> Mise à niveau des mots parasites à partir de SQL Server 2005  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Les mots parasites ont été remplacés par les mots vides. Lorsqu'une base de données est mise à niveau à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les fichiers de mots parasites ne sont plus utilisés. Toutefois, les fichiers de mots parasites sont stockés dans le dossier FTDATA\ FTNoiseThesaurusBak, et vous pouvez les utiliser ultérieurement lors de la mise à jour ou de la génération des listes de mots vides correspondantes. Pour plus d’informations sur la mise à niveau de fichiers de mots parasites en listes de mots vides, consultez [Mise à niveau de la fonction de recherche en texte intégral](../../relational-databases/search/upgrade-full-text-search.md).  
  
 [Dans cette rubrique](#TOP)  
  
  