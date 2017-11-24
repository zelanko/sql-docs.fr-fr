---
title: Excel Source | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelsource.f1
- sql13.dts.designer.excelsourceadapter.connection.f1
- sql13.dts.designer.excelsourceadapter.columns.f1
- sql13.dts.designer.excelsourceadapter.erroroutput.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
caps.latest.revision: 60
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: e8b5878513b74faa8df5e7766762f2f7287ec7af
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

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
  
 La source Excel utilise à un gestionnaire de connexions Excel pour se connecter à une source de données ; ce gestionnaire spécifie le classeur à utiliser. Pour plus d'informations, consultez [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md).  
  
 La source Excel a une sortie normale et une sortie d'erreur.  
  
## <a name="usage-considerations"></a>Considérations sur l'utilisation  
 Le gestionnaire de connexions Excel utilise le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour Jet version 4.0 et son pilote de prise en charge Excel ISAM (Indexed Sequential Access Method) pour se connecter puis lire et écrire les données dans les sources de données Excel.  
  
 De nombreux articles disponibles dans la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] documentent le comportement de ce fournisseur et de ce pilote et, bien que ces articles ne soient pas spécifiques à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou à son prédécesseur DTS (Data Transformation Services), vous pouvez souhaiter vous informer sur certains comportements susceptibles de produire des résultats inattendus. Pour obtenir des informations générales sur l'utilisation et le comportement du pilote Excel, consultez [COMMENT FAIRE : Utiliser ADO avec des données Excel à partir de Visual Basic ou de VBA](http://support.microsoft.com/kb/257819).  
  
 Les comportements suivants du fournisseur Jet associé au pilote Excel peuvent produire des résultats inattendus lors de la lecture des données à partir d'une source de données Excel.  
  
-   **Sources de données**. Dans un classeur Excel, la source de données peut être une feuille de calcul, à laquelle le signe « $ » doit être ajouté (par exemple, « Feuille1$ ») ou une plage nommée (par exemple, « MaPlage »). Dans une instruction SQL, le nom d'une feuille de calcul doit être délimité (par exemple, « [Feuille1$] ») afin que le signe « $ » ne provoque pas une erreur de syntaxe. Le générateur de requêtes ajoute automatiquement ces délimiteurs. Lorsque vous spécifiez une feuille de calcul ou une plage, le pilote lit le bloc de cellules contigu, à partir de la première cellule non vide dans l'angle supérieur gauche de la feuille de calcul ou de la plage. Par conséquent, il ne peut pas y avoir de ligne vide dans les données source, ni entre les lignes de titre ou d'en-tête et les lignes de données.  
  
-   **Valeurs manquantes**. Le pilote Excel lit un certain nombre de lignes (par défaut, 8 lignes) dans la source spécifiée afin de déterminer le type de données de chaque colonne. Lorsqu'il s'avère qu'une colonne combine différents types de données, notamment des données numériques avec des données texte, le pilote porte son choix sur le type de données majoritaire et retourne des valeurs NULL dans les cellules qui contiennent des données de l'autre type. En cas d'égalité, le type numérique l'emporte. La plupart des options de mise en forme de cellule dans la feuille de calcul Excel n'affectent pas cette détermination du type de données. Vous pouvez modifier ce comportement du pilote Excel en spécifiant le mode d'importation. Pour spécifier le mode d’importation, ajoutez **IMEX=1** à la valeur de Propriétés étendues dans la chaîne de connexion du gestionnaire de connexions Excel dans la fenêtre **Propriétés** . Pour plus d’informations, consultez [PRB: valeurs Excel retournées en tant que valeurs NULL à l’aide de DAO OpenRecordset](http://support.microsoft.com/kb/194124).  
  
-   **Texte tronqué**. Lorsque le pilote détermine qu'une colonne Excel contient des données texte, il sélectionne le type de données (string ou memo) en fonction de la valeur la plus longue qu'il échantillonne. Si le pilote ne découvre pas de valeurs comptant plus de 255 caractères dans les lignes échantillonnées, il traite la colonne comme une colonne de type string à 255 caractères et non comme une colonne de type memo. Par conséquent, les valeurs de plus de 255 caractères peuvent être tronquées. Pour importer des données à partir d'une colonne de type memo sans troncation, vous devez vous assurer que la colonne de type memo dans au moins une des lignes échantillonnées contient une valeur comptant plus de 255 caractères, sinon, vous devez augmenter le nombre de lignes échantillonnées par le pilote pour inclure une telle ligne. Vous pouvez augmenter le nombre de lignes échantillonnées en augmentant la valeur de **TypeGuessRows** sous la clé de Registre **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** . Pour plus d’informations, consultez [PRB : échec de transfert de données de source Jet 4.0 OLEDB avec erreur de dépassement de mémoire tampon](http://support.microsoft.com/kb/281517).  
  
-   **Types de données système**. Le pilote Excel ne reconnaît qu'un ensemble limité de types de données. Par exemple, toutes les colonnes numériques sont interprétées comme doubles (DT_R8) et toutes les colonnes de type chaîne (autres que les colonnes mémo) comme des chaînes Unicode de 255 caractères (DT_WSTR). [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] mappe les types de données Excel de la façon suivante :  
  
    -   Numérique – virgule flottante à double précision (DT_R8)  
  
    -   Devise – devise (DT_CY)  
  
    -   Booléen – booléen (DT_BOOL)  
  
    -   Date/heure – **datetime** (DT_DATE)  
  
    -   Chaîne – chaîne Unicode, longueur 255 (DT_WSTR)  
  
    -   Mémo – flux de texte Unicode (DT_NTEXT)  
  
-   **Conversions des types de données et des longueurs**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne convertit pas implicitement les types de données. Vous devrez donc éventuellement utiliser des transformations Colonne dérivée ou Conversion de données pour convertir les données Excel explicitement avant de les charger dans une destination non-Excel, ou pour convertir des données non-Excel avant de les charger dans une destination Excel. Dans ce cas, il peut être utile de créer le package initial à l'aide de l'Assistant Importation et Exportation, qui configure les conversions nécessaires automatiquement. Des exemples de conversions pouvant être requises sont présentées ci-dessous :  
  
    -   Conversion entre des colonnes Excel de type string Unicode et des colonnes de type string non-Unicode avec des pages de codes spécifiques.  
  
    -   Conversion entre des colonnes Excel de type string à 255 caractères et des colonnes de type string de longueurs différentes.  
  
    -   Conversion entre des colonnes numériques Excel à double précision et des colonnes numériques d'autres types.  
  
## <a name="excel-source-configuration"></a>Configuration d'une source Excel  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète toutes les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées d'Excel](../../integration-services/data-flow/excel-custom-properties.md)  
  
 Pour plus d’informations sur le bouclage dans un groupe de fichiers Excel, consultez [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Mapper des paramètres de requête à des variables dans un composant de flux de données](../../integration-services/data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [Définir les propriétés d'un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Trier des données pour les transformations de fusion et de jointure de fusion](../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [Boucle via Excel fichiers et les Tables à l’aide d’un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
## <a name="excel-source-editor-connection-manager-page"></a>Éditeur de source Excel (page Gestionnaire de connexions)
  Le nœud **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source Excel** vous permet de sélectionner le classeur [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] de la source à utiliser. La source Excel lit les données à partir d'une feuille de calcul ou d'une plage nommée dans un classeur existant.  
  
> [!NOTE]  
>  La propriété **CommandTimeout** de la source Excel n’est pas disponible dans **l’Éditeur de source Excel**, mais peut être définie à l’aide de **l’Éditeur avancé**. Pour plus d’informations sur cette propriété, consultez la section sur la source Excel dans [Propriétés personnalisées d’Excel](../../integration-services/data-flow/excel-custom-properties.md).  
  
### <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions Excel existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Gestionnaire de connexions Excel** .  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Value|Description|  
|-----------|-----------------|  
|Table ou vue|Récupérez des données à partir d'une feuille de calcul ou d'une plage nommée dans le fichier Excel.|  
|Variable de nom de table ou de vue|Spécifiez le nom de la feuille de calcul ou de la plage dans une variable.<br /><br /> **Informations connexes :** [Utiliser des variables dans des packages](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)|  
|Commande SQL|Récupérez des données à partir du fichier Excel à l'aide d'une requête SQL. |  
|Commande SQL à partir d'une variable|Spécifiez le texte de la requête SQL dans une variable.|  
  
 **Aperçu**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Vue de données** . L'aperçu peut afficher jusqu'à 200 lignes.  
  
### <a name="data-access-mode-dynamic-options"></a>Options dynamiques du mode d'accès aux données  
  
#### <a name="data-access-mode--table-or-view"></a>Mode d'accès aux données = Table ou vue  
 **Nom de la feuille Excel**  
 Sélectionnez le nom de la feuille de calcul ou de la plage nommée dans la liste des éléments disponibles dans le classeur Excel.  
  
#### <a name="data-access-mode--table-name-or-view-name-variable"></a>Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable contenant le nom de la feuille de calcul ou de la plage nommée.  
  
#### <a name="data-access-mode--sql-command"></a>Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte d’une requête SQL, créez la requête en cliquant sur **Générer une requête**ou parcourez l’arborescence jusqu’au fichier qui contient le texte de la requête en cliquant sur **Parcourir**.  
  
 **Paramètres**  
 Si vous avez entré une requête paramétrable en spécifiant ? comme espace réservé de paramètre dans le texte de la requête, utilisez la boîte de dialogue **Définition des paramètres de la requête** pour mapper des paramètres d’entrée de la requête à des variables du package.  
  
 **Build query**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , localisez le fichier contenant le texte de la requête SQL.  
  
 **Analyser la requête**  
 Vérifiez la syntaxe du texte de la requête.  
  
#### <a name="data-access-mode--sql-command-from-variable"></a>Mode d'accès aux données = Commande SQL à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le texte de la requête SQL.  
  
## <a name="excel-source-editor-columns-page"></a>Éditeur de source Excel (page Colonnes)
  La page **Colonnes** de la boîte de dialogue **Éditeur de source Excel** vous permet de mapper une colonne de sortie à chaque colonne externe (source).  
  
### <a name="options"></a>Options  
 **Colonnes externes disponibles**  
 Affiche la liste des colonnes externes disponibles dans la source de données. Vous ne pouvez pas ajouter ou supprimer des colonnes à l'aide de cette table.  
  
 **Colonne externe**  
 Affiche les colonnes externes (sources) dans l'ordre de lecture de la tâche. Vous pouvez modifier cet ordre en désactivant les colonnes sélectionnées dans la table mentionnée ci-dessus, puis en sélectionnant les colonnes externes dans la liste, dans un ordre différent.  
  
 **Colonne de sortie**  
 Spécifiez un nom unique pour chaque colonne de sortie. Le nom par défaut est celui de la colonne externe (source) sélectionnée ; vous pouvez néanmoins choisir n'importe quel nom unique et significatif. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
## <a name="excel-source-editor-error-output-page"></a>Éditeur de source Excel (page Sortie d'erreur)
  La page **Sortie d’erreur** de la boîte de dialogue **Éditeur de source Excel** vous permet de sélectionner les options de gestion des erreurs et de définir les propriétés sur les colonnes de sortie d’erreur.  
  
### <a name="options"></a>Options  
 **Entrée ou Sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Indique les colonnes externes (source) que vous avez sélectionnées à la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source Excel**.  
  
 **Erreur**  
 Indiquez ce qui doit se produire lorsqu'une erreur se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Rubriques connexes :** [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **Troncation**  
 Indiquez ce qui doit se produire lorsqu'une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Affiche la description de l'erreur.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Indiquez ce qui doit se produire pour l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="related-content"></a>Contenu connexe  
  
-   Entrée de blog, [Importing data from 64-bit Excel in SSIS](http://go.microsoft.com/fwlink/?LinkId=217673), sur hrvoje.piasevoli.com  
  
-   Entrée de blog, [Excel in Integration Services, Part 1 of 3: Connections and Components](http://go.microsoft.com/fwlink/?LinkId=217674), sur dougbert.com  
  
-   Entrée de blog, [Excel in Integration Services, Part 2 of 3: Tables and Data Types](http://go.microsoft.com/fwlink/?LinkId=217675), sur dougbert.com.  
  
-   Entrée de blog, [Excel in Integration Services, Part 3 of 3: Issues and Alternatives](http://go.microsoft.com/fwlink/?LinkId=217676), sur dougbert.com.  
  
  

