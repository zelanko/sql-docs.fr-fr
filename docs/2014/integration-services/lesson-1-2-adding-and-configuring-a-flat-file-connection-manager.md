---
title: 'Étape 2 : Ajout et configuration d’un gestionnaire de connexions de fichiers plats | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9a77dd32-d8c2-4961-ad37-2a971f9d6043
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0c6cd41be722d80baf442db907d6fdab9f334859
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62891788"
---
# <a name="step-2-adding-and-configuring-a-flat-file-connection-manager"></a>Étape 2 : ajout et configuration d'un gestionnaire de connexions de fichiers plats
  Dans cette tâche, vous ajoutez un gestionnaire de connexions de fichiers plats au package que vous venez de créer. Un gestionnaire de connexions de fichiers plats permet à un package d'extraire des données d'un fichier plat. Grâce à ce Gestionnaire, vous pouvez spécifier le nom et l'emplacement du fichier, les paramètres régionaux et la page de codes et enfin, le format du fichier, y compris les séparateurs de colonnes, à appliquer lorsque le package extrait les données du fichier plat. Par ailleurs, vous pouvez spécifier manuellement le type de données pour les colonnes individuelles ou utiliser la boîte de dialogue **Suggérer les types de colonnes** pour mapper automatiquement les colonnes de données extraites aux types de données [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Vous devez créer un nouveau gestionnaire de connexions de fichiers plats pour chaque format de fichier utilisé. Étant donné que ce didacticiel extrait des données à partir de plusieurs fichiers plats qui ont exactement le même format de données, il vous faudra ajouter et configurer un seul gestionnaire de connexions de fichiers plats uniquement pour votre package.  
  
 Pour les besoins de ce didacticiel, vous allez configurer les propriétés suivantes dans votre gestionnaire de connexions de fichiers plats :  
  
-   **Noms des colonnes :** Étant donné que le fichier plat ne contient pas de noms de colonnes, le gestionnaire de connexions de fichiers plats crée des noms de colonnes par défaut. Ces noms par défaut ne servent pas à identifier ce que représente chaque colonne. Pour que ces noms par défaut soient plus significatifs, vous devez les remplacer par ceux qui correspondent à la table de faits dans laquelle les données du fichier plat doivent être chargées.  
  
-   **Mappages de données :** Les mappages de types de données que vous spécifiez pour le gestionnaire de connexions de fichiers plats seront utilisés par tous les composants de source de données de fichier plat qui font référence au gestionnaire de connexions. Vous pouvez choisir de mapper les types de données manuellement en utilisant le gestionnaire de connexions de fichiers plats ou bien d’utiliser la boîte de dialogue **Suggérer les types de colonnes** . Dans ce didacticiel, vous visualisez les mappages suggérés dans la boîte de dialogue **Suggérer les types de colonnes** , puis vous créez manuellement les mappages nécessaires dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** .  
  
 Le gestionnaire de connexions de fichiers plats fournit des informations de paramètres régionaux sur le fichier de données. Si votre ordinateur n’est pas configuré pour utiliser l’option régional anglais (États-Unis), vous devez définir des propriétés supplémentaires dans la boîte de dialogue **éditeur du gestionnaire de connexions de fichiers plats** .  
  
### <a name="to-add-a-flat-file-connection-manager-to-the-ssis-package"></a>Pour ajouter un gestionnaire de connexions de fichiers plats au package SSIS  
  
1.  Cliquez avec le bouton droit dans la zone **Gestionnaires de connexions** , puis cliquez sur **Nouvelle connexion de fichier plat**.  
  
2.  Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** , pour **Nom du gestionnaire de connexions**, tapez **Sample Flat File Source Data**.  
  
3.  Cliquez sur **Parcourir**.  
  
4.  Dans la boîte de dialogue **Ouvrir** , accédez au fichier SampleCurrencyData.txt sur votre ordinateur.  
  
     Ces données exemple sont incluses dans les packages de leçons [!INCLUDE[ssIS](../includes/ssis-md.md)] . Pour télécharger ces exemples de données et les packages de leçons, procédez comme suit.  
  
    1.  Accéder aux [exemples de produits Integration Services](https://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l'onglet **DOWNLOADS** (Téléchargements).  
  
    3.  Cliquez sur le fichier SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Désélectionnez la case à cocher Noms des colonnes dans la première ligne de données.  
  
### <a name="to-set-locale-sensitive-properties"></a>Pour définir des propriétés de paramètres régionaux  
  
1.  Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** , cliquez sur **Général**.  
  
2.  Définissez **paramètres régionaux** sur anglais (États-Unis) et **page de codes** sur 1252.  
  
### <a name="to-rename-columns-in-the-flat-file-connection-manager"></a>Pour renommer les colonnes dans le gestionnaire de connexions de fichiers plats  
  
1.  Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** , cliquez sur **Avancé**.  
  
2.  Dans le volet des propriétés, apportez les modifications suivantes :  
  
    -   Remplacez la valeur de la propriété nom `AverageRate`de la **colonne 0** par.  
  
    -   Remplacez la valeur de la propriété **Column 1** Name par `CurrencyID`.  
  
    -   Remplacez la valeur de la propriété nom `CurrencyDate`de la **colonne 2** par.  
  
    -   Remplacez la valeur de la propriété **Column 3** Name par `EndOfDayRate`.  
  
    > [!NOTE]  
    >  Par défaut, ces quatre colonnes ont initialement le type de données string [DT_STR] avec une `OutputColumnWidth` égale à 50.  
  
### <a name="to-remap-column-data-types"></a>Pour remapper les types de données des colonnes  
  
1.  Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** , cliquez sur **Suggérer les types**.  
  
     
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggère automatiquement les types de données les plus appropriés en se basant sur les 200 premières lignes de données. Vous pouvez aussi modifier les options de suggestion et augmenter ou réduire l'échantillon de données, spécifier le type de données par défaut pour les entiers ou les données booléennes ou bien ajouter des espaces pour séparer les colonnes de type chaîne.  
  
     Pour l’instant, n’apportez aucune modification aux options de la boîte de dialogue **Suggérer les types de colonnes** et cliquez sur **OK** pour que [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggère des types de données pour les colonnes. Ceci vous ramène au volet **Avancé** de la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats** où vous pouvez afficher les types de données pour les colonnes suggérés par [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. (Si vous cliquez sur **Annuler**, aucune suggestion n’est faite pour les métadonnées des colonnes, et le type de données chaîne par défaut (DT_STR) est utilisé.)  
  
     Dans ce didacticiel, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggère les types de données montrées dans la deuxième colonne de la table ci-dessous pour les données issues du fichier SampleCurrencyData.txt. Toutefois, les types de données requis pour les colonnes dans la destination, qui seront définis ultérieurement, sont montrés dans la dernière colonne de la table suivante.  
  
    |Colonne de fichier plat|Type suggéré|Colonne de destination|Type de destination|  
    |----------------------|--------------------|------------------------|----------------------|  
    |AverageRate|float [DT_R4]|FactCurrency.AverageRate|float|  
    |CurrencyID|string [DT_STR]|DimCurrency.CurrencyAlternateKey|nchar(3)|  
    |CurrencyDate|date [DT_DATE]|DimDate.FullDateAlternateKey|Date|  
    |EndOfDayRate|float [DT_R4]|FactCurrency.EndOfDayRate|float|  
  
     Le type de données suggéré pour `CurrencyID` la colonne n’est pas compatible avec le type de données du champ dans la table de destination. Étant donné que le type `DimCurrency.CurrencyAlternateKey` de données de est nchar ( `CurrencyID` 3), il doit être modifié de String [DT_STR] en String [DT_WSTR]. En outre, le champ `DimDate.FullDateAlternateKey` est défini en tant que type de données date ; par conséquent `CurrencyDate` , doit passer de la date [DT_DATE] à la date de la base de données [DT_DBDATE].  
  
2.  Dans la liste, sélectionnez la colonne CurrencyID et, dans le volet de propriétés, modifiez le type de `CurrencyID` données de la colonne de chaîne [DT_STR] en chaîne Unicode [DT_WSTR].  
  
3.  Dans le volet de propriétés, modifiez le type de données `CurrencyDate` de la colonne date [DT_DATE] en date de la base de données [DT_DBDATE].  
  
4.  Cliquez sur **OK**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 3 : ajout et configuration d'un gestionnaire de connexions OLE DB](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de connexions de fichiers plats](connection-manager/file-connection-manager.md)   
 [Types de données d'Integration Services](data-flow/integration-services-data-types.md)  
  
  
