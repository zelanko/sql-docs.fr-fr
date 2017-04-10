---
title: "Destination Excel | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.exceldest.f1"
helpviewer_keywords: 
  - "destinations [Integration Services], Excel"
  - "Excel [Integration Services]"
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# Destination Excel
  La destination Excel charge les données dans des feuilles de calcul ou des plages au sein de classeurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.  
  
## Modes d'accès  
 La destination Excel propose trois modes d'accès différents pour charger les données :  
  
-   Une table ou une vue.  
  
-   Une table ou une vue spécifiée dans une variable.  
  
-   Les résultats d'une instruction SQL. La requête peut être une requête paramétrable.  
  
> [!IMPORTANT]  
>  Dans Excel, une feuille de calcul ou une plage sont l'équivalent d'une table ou d'une vue. Les listes de tables disponibles dans l'Éditeur de source Excel et l'Éditeur de destination Excel contiennent uniquement les feuilles de calcul (identifiées par le signe $ qui est ajouté au nom de la feuille de calcul, comme dans Feuille1$) et plages nommées (identifiées par l'absence de signe $, comme dans MaPlage) existantes.  
  
## Considérations sur l'utilisation  
 Le gestionnaire de connexions Excel utilise le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour Jet version 4.0 et son pilote de prise en charge Excel ISAM (Indexed Sequential Access Method) pour se connecter puis lire et écrire les données dans les sources de données Excel.  
  
 De nombreux articles disponibles dans la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] documentent le comportement de ce fournisseur et de ce pilote et, bien que ces articles ne soient pas spécifiques à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou à son prédécesseur DTS (Data Transformation Services), vous pouvez souhaiter vous informer sur certains comportements susceptibles de produire des résultats inattendus. Pour obtenir des informations générales sur l'utilisation et le comportement du pilote Excel, consultez [COMMENT FAIRE : Utiliser ADO avec des données Excel à partir de Visual Basic ou de VBA](http://support.microsoft.com/kb/257819).  
  
 Les comportements suivants du fournisseur Jet inclus avec le pilote Excel peuvent provoquer des résultats inattendus lors de l'enregistrement des données vers une destination Excel.  
  
-   **Enregistrement des données texte**. Lorsque le pilote Excel enregistre des valeurs de données texte vers une destination Excel, le pilote fait précéder le texte contenu dans chaque cellule de l'apostrophe (') pour que les valeurs enregistrées soient bien interprétées comme des valeurs texte. Si vous possédez ou développez des applications qui lisent ou traitent les données enregistrées, peut-être serez-vous amené, dans ce cas précis, à inclure un traitement spécial pour l'apostrophe.  
  
     Pour plus d'informations sur la façon d'inclure l'apostrophe, consultez le billet de blog, [Une apostrophe est ajoutée à toutes les chaînes quand des données sont transformées dans excel lors de l'utilisation d'un composant de flux de données de destination Excel dans un package SSIS](http://go.microsoft.com/fwlink/?LinkId=400876), sur msdn.com.  
  
-   **Enregistrement des données mémo (ntext)**. Avant de pouvoir enregistrer des chaînes dépassant 255 caractères dans une colonne Excel, le pilote doit reconnaître le type de données de la colonne de destination comme **mémo** et non comme **chaîne**. Si la table de destination contient déjà des lignes de données, les premières lignes échantillonnées par le pilote doivent contenir au moins une instance d'une valeur dépassant 255 caractères dans la colonne mémo. Si la table de destination est créée pendant la conception du package ou au moment de l'exécution, l'instruction CREATE TABLE doit utiliser LONGTEXT (ou un de ses synonymes) comme type de données de la colonne mémo.  
  
-   **Types de données système**. Le pilote Excel ne reconnaît qu'un ensemble limité de types de données. Par exemple, toutes les colonnes numériques sont interprétées comme doubles (DT_R8) et toutes les colonnes de type chaîne (autres que les colonnes mémo) comme des chaînes Unicode de 255 caractères (DT_WSTR). [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] mappe les types de données Excel de la façon suivante :  
  
    -   Numérique    virgule flottante double précision (DT_R8)  
  
    -   Devise     devise (DT_CY)  
  
    -   Booléen     booléen (DT_BOOL)  
  
    -   Date/heure     **datetime** (DT_DATE)  
  
    -   Chaîne     chaîne Unicode, longueur 255 (DT_WSTR)  
  
    -   Mémo     flux de texte Unicode (DT_NTEXT)  
  
-   **Conversions des types de données et des longueurs**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne convertit pas implicitement les types de données. Par conséquent, peut-être devrez-vous utiliser les transformations de conversion de données et de colonne dérivée pour convertir explicitement des données Excel avant chargement dans une destination non-Excel ou pour convertir des données non-Excel avant chargement dans une destination Excel. Dans ce cas, il peut être utile de créer le package initial à l'aide de l'Assistant Importation et Exportation, qui configure les conversions nécessaires automatiquement. Des exemples de conversions pouvant être requises sont présentées ci-dessous :  
  
    -   conversion entre des colonnes Unicode Excel de type chaîne et des colonnes non-Unicode de type chaîne avec des pages de codes spécifiques ;  
  
    -   conversion entre des colonnes Excel de type chaîne de 255 caractères et des colonnes de type chaîne de longueurs différentes ;  
  
    -   conversion entre des colonnes numériques Excel à double précision et des colonnes numériques d'autres types.  
  
## Configuration de la destination Excel  
 La destination Excel utilise un gestionnaire de connexions Excel pour se connecter à une source de données et le gestionnaire de connexions indique le fichier de feuille de calcul à utiliser. Pour plus d'informations, consultez [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md).  
  
 La destination Excel comporte une entrée normale et une sortie d'erreur.  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de destination Excel** , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de destination Excel &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/excel-destination-editor-connection-manager-page.md)  
  
-   [Éditeur de destination Excel &#40;page Mappages&#41;](../../integration-services/data-flow/excel-destination-editor-mappings-page.md)  
  
-   [Éditeur de destination Excel &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/excel-destination-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète toutes les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../Topic/Common%20Properties.md)  
  
-   [Propriétés personnalisées d'Excel](../../integration-services/data-flow/excel-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## Tâches associées  
  
-   [Établir une connexion à un classeur Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
-   [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Définir les propriétés d'un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## Contenu connexe  
  
-   Entrée de blog, [Excel in Integration Services, Part 1 of 3: Connections and Components](http://go.microsoft.com/fwlink/?LinkId=217674), sur dougbert.com  
  
-   Entrée de blog, [Excel in Integration Services, Part 2 of 3: Tables and Data Types](http://go.microsoft.com/fwlink/?LinkId=217675), sur dougbert.com.  
  
-   Entrée de blog, [Excel in Integration Services, Part 3 of 3: Issues and Alternatives](http://go.microsoft.com/fwlink/?LinkId=217676), sur dougbert.com.  
  
## Voir aussi  
 [Source Excel](../../integration-services/data-flow/excel-source.md)   
 [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)   
 [Flux de données](../../integration-services/data-flow/data-flow.md)   
 [Utilisation de fichiers Excel avec la tâche de script](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  