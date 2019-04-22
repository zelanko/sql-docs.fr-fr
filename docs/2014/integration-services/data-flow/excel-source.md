---
title: Source Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsource.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 15ef45a4f3bfb0b74de2472a5b2f0d8e483edab1
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59242257"
---
# <a name="excel-source"></a>Source Excel
  La source Excel extrait des données de feuilles de calcul ou de plages dans des classeurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.  
  
 La source Excel fournit quatre modes d'accès aux données différents pour l'extraction des données :  
  
-   Une table ou une vue.  
  
-   Une table ou une vue spécifiée dans une variable.  
  
-   Les résultats d'une instruction SQL. La requête peut être une requête paramétrable.  
  
-   Les résultats d'une instruction SQL stockée dans une variable.  
  
> [!IMPORTANT]  
>  Dans Excel, une feuille de calcul ou une plage sont l'équivalent d'une table ou d'une vue. La listes de tables disponibles dans les éditeurs de source et de destination Excel n'affiche que des feuilles de calcul existantes (identifiées par le signe « $ » à la fin du nom de la feuille de calcul, par exemple « Feuille1$ ») et des plages nommées (signalées par l'absence du signe « $ », par exemple « MaPlage »). Pour plus d'informations, consultez la section Considérations sur l'utilisation.  
  
 La source Excel utilise à un gestionnaire de connexions Excel pour se connecter à une source de données ; ce gestionnaire spécifie le classeur à utiliser. Pour plus d'informations, consultez [Excel Connection Manager](../connection-manager/excel-connection-manager.md).  
  
 La source Excel a une sortie normale et une sortie d'erreur.  
  
## <a name="usage-considerations"></a>Considérations sur l'utilisation  
 Le gestionnaire de connexions Excel utilise le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour Jet version 4.0 et son pilote de prise en charge Excel ISAM (Indexed Sequential Access Method) pour se connecter puis lire et écrire les données dans les sources de données Excel.  
  
 De nombreux articles disponibles dans la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] documentent le comportement de ce fournisseur et de ce pilote et, bien que ces articles ne soient pas spécifiques à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou à son prédécesseur DTS (Data Transformation Services), vous pouvez souhaiter vous informer sur certains comportements susceptibles de produire des résultats inattendus. Pour obtenir des informations générales sur l’utilisation et le comportement du pilote Excel, consultez [HOWTO : Utiliser ADO avec des données Excel à partir de Visual Basic ou VBA](https://support.microsoft.com/kb/257819).  
  
 Les comportements suivants du fournisseur Jet associé au pilote Excel peuvent produire des résultats inattendus lors de la lecture des données à partir d'une source de données Excel.  
  
-   **Sources de données**. Dans un classeur Excel, la source de données peut être une feuille de calcul, à laquelle le signe « $ » doit être ajouté (par exemple, « Feuille1$ ») ou une plage nommée (par exemple, « MaPlage »). Dans une instruction SQL, le nom d'une feuille de calcul doit être délimité (par exemple, « [Feuille1$] ») afin que le signe « $ » ne provoque pas une erreur de syntaxe. Le générateur de requêtes ajoute automatiquement ces délimiteurs. Lorsque vous spécifiez une feuille de calcul ou une plage, le pilote lit le bloc de cellules contigu, à partir de la première cellule non vide dans l'angle supérieur gauche de la feuille de calcul ou de la plage. Par conséquent, il ne peut pas y avoir de ligne vide dans les données source, ni entre les lignes de titre ou d'en-tête et les lignes de données.  
  
-   **Valeurs manquantes**. Le pilote Excel lit un certain nombre de lignes (par défaut, 8 lignes) dans la source spécifiée afin de déterminer le type de données de chaque colonne. Lorsqu'il s'avère qu'une colonne combine différents types de données, notamment des données numériques avec des données texte, le pilote porte son choix sur le type de données majoritaire et retourne des valeurs NULL dans les cellules qui contiennent des données de l'autre type. En cas d'égalité, le type numérique l'emporte. La plupart des options de mise en forme de cellule dans la feuille de calcul Excel n'affectent pas cette détermination du type de données. Vous pouvez modifier ce comportement du pilote Excel en spécifiant le mode d'importation. Pour spécifier le Mode d’importation, ajoutez `IMEX=1` à la valeur de propriétés étendues dans la chaîne de connexion du Gestionnaire de connexions Excel dans le **propriétés** fenêtre. Pour plus d’informations, consultez [PRB : Excel les valeurs retournées comme NULL à l’aide de DAO OpenRecordset](https://support.microsoft.com/kb/194124).  
  
-   **Texte tronqué**. Lorsque le pilote détermine qu'une colonne Excel contient des données texte, il sélectionne le type de données (string ou memo) en fonction de la valeur la plus longue qu'il échantillonne. Si le pilote ne découvre pas de valeurs comptant plus de 255 caractères dans les lignes échantillonnées, il traite la colonne comme une colonne de type string à 255 caractères et non comme une colonne de type memo. Par conséquent, les valeurs de plus de 255 caractères peuvent être tronquées. Pour importer des données à partir d'une colonne de type memo sans troncation, vous devez vous assurer que la colonne de type memo dans au moins une des lignes échantillonnées contient une valeur comptant plus de 255 caractères, sinon, vous devez augmenter le nombre de lignes échantillonnées par le pilote pour inclure une telle ligne. Vous pouvez augmenter le nombre de lignes échantillonnées en augmentant la valeur de **TypeGuessRows** sous la clé de Registre **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** . Pour plus d’informations, consultez [PRB : Échec de transfert de données à partir de la Source de Jet 4.0 OLEDB avec erreur](https://support.microsoft.com/kb/281517).  
  
-   **Types de données système**. Le pilote Excel ne reconnaît qu'un ensemble limité de types de données. Par exemple, toutes les colonnes numériques sont interprétées comme doubles (DT_R8) et toutes les colonnes de type chaîne (autres que les colonnes mémo) comme des chaînes Unicode de 255 caractères (DT_WSTR). [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] mappe les types de données Excel de la façon suivante :  
  
    -   Numérique - virgule flottante double précision (DT_R8)  
  
    -   Devise - devise (DT_CY)  
  
    -   Booléen - booléen (DT_BOOL)  
  
    -   Date/heure - `datetime` (DT_DATE)  
  
    -   Chaîne - chaîne Unicode, longueur 255 (DT_WSTR)  
  
    -   Mémo - flux de texte Unicode (DT_NTEXT)  
  
-   **Conversions des types de données et des longueurs**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne convertit pas implicitement les types de données. Vous devrez donc éventuellement utiliser des transformations Colonne dérivée ou Conversion de données pour convertir les données Excel explicitement avant de les charger dans une destination non-Excel, ou pour convertir des données non-Excel avant de les charger dans une destination Excel. Dans ce cas, il peut être utile de créer le package initial à l'aide de l'Assistant Importation et Exportation, qui configure les conversions nécessaires automatiquement. Des exemples de conversions pouvant être requises sont présentées ci-dessous :  
  
    -   Conversion entre des colonnes Excel de type string Unicode et des colonnes de type string non-Unicode avec des pages de codes spécifiques.  
  
    -   Conversion entre des colonnes Excel de type string à 255 caractères et des colonnes de type string de longueurs différentes.  
  
    -   Conversion entre des colonnes numériques Excel à double précision et des colonnes numériques d'autres types.  
  
## <a name="excel-source-configuration"></a>Configuration d'une source Excel  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de source Excel** , cliquez sur l’une des rubriques suivantes :  
  
-   [Éditeur de source Excel &#40;page Gestionnaire de connexions&#41;](../excel-source-editor-connection-manager-page.md)  
  
-   [Éditeur de source Excel &#40;page Colonnes&#41;](../excel-source-editor-columns-page.md)  
  
-   [Éditeur de source Excel &#40;page Sortie d’erreur&#41;](../excel-source-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète toutes les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées d'Excel](excel-custom-properties.md)  
  
 Pour plus d’informations sur le bouclage dans un groupe de fichiers Excel, consultez [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../control-flow/foreach-loop-container.md).  
  
## <a name="related-tasks"></a>Tâches associées  

-   [Importer des données à partir d’Excel ou exporter des données vers Excel avec SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)

-   [Mapper des paramètres de requête à des variables dans un composant de flux de données](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../control-flow/foreach-loop-container.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Entrée de blog, [Importing data from 64-bit Excel in SSIS](https://go.microsoft.com/fwlink/?LinkId=217673), sur hrvoje.piasevoli.com  
  
-   Entrée de blog, [Excel in Integration Services, partie 1 sur 3 : Connections and Components](https://go.microsoft.com/fwlink/?LinkId=217674), sur dougbert.com  
  
-   Entrée de blog, [Excel in Integration Services, Part 2 of 3 : Types de données et tables](https://go.microsoft.com/fwlink/?LinkId=217675), sur dougbert.com.  
  
-   Entrée de blog, [Excel in Integration Services, partie 3 sur 3 : Issues and Alternatives](https://go.microsoft.com/fwlink/?LinkId=217676), sur dougbert.com.  
  
-   Entrée de blog, [connexion à Excel (XLSX) dans SSIS ](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html).  
  
  
