---
title: Data Streaming Destination | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL11.DTS.DESIGNER.DATASTREAMINGDEST.F1
ms.assetid: 640e6a19-49ae-4ee8-ac07-008370158f0e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3dd1ae26ab126e87a8f239597a573d24dbc8b3e1
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86916759"
---
# <a name="data-streaming-destination"></a>Data Streaming Destination

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  **Data Streaming Destination** est un composant de destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) qui permet au **fournisseur OLE DB pour SSIS** de consommer la sortie d’un package SSIS sous la forme d’un jeu de résultats tabulaire. Vous pouvez créer un serveur lié qui utilise le fournisseur OLE DB pour SSIS, puis exécuter une requête SQL sur le serveur lié pour afficher les données retournées par le package SSIS.  
  
 Dans l’exemple suivant, la requête suivante retourne une sortie du package Package.dtsx dans le projet SSISPackagePublishing dans le dossier Power BI du catalogue SSIS. Cette requête utilise le serveur lié nommé [serveur lié par défaut pour Integration Services] qui à son tour utilise le nouveau fournisseur OLE DB pour SSIS. La requête inclut le nom du dossier, le nom du projet et le nom du package dans le catalogue SSIS. Le fournisseur OLE DB pour SSIS exécute le package que vous avez spécifié dans la requête et retourne le jeu de résultats tabulaire.  
  
```sql
SELECT * FROM OPENQUERY([Default Linked Server for Integration Services], N'Folder=Power BI;Project=SSISPackagePublishing;Package=Package.dtsx')  
  
```  
  
## <a name="data-feed-publishing-components"></a>Composants de publication du flux de données  
 Les composants de publication de flux de données sont notamment les suivants : fournisseur OLE DB pour SSIS, Data Streaming Destination et Assistant de publication du package SSIS. L’Assistant vous permet de publier un package SSIS sous la forme d’une vue SQL dans une instance de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L’Assistant vous aide à créer un serveur lié qui utilise le fournisseur OLE DB pour SSIS et une vue SQL qui représente une requête sur le serveur lié. Vous exécutez la vue pour interroger les résultats du package SSIS comme un jeu de données tabulaire.  
  
 Pour vérifier que le fournisseur SSISOLEDB est installé, dans SQL Server Management Studio, développez **Objets serveur**, **Serveurs liés**, **Fournisseurs**et vérifiez que le fournisseur **SSISOLEDB** est affiché. Double-cliquez sur **SSISOLEDB**, activez **Autoriser Inprocess** si ce n’est pas déjà fait, puis cliquez sur **OK**.  
  
## <a name="publish-an-ssis-package-as-a-sql-view"></a>Publication d’un package SSIS sous la forme d’une vue SQL  
 La procédure suivante décrit les étapes pour publier un package SSIS sous la forme d’une vue SQL.  
  
1.  Créez un package SSIS avec un composant **Data Streaming Destination** et déployez le package dans le catalogue SSIS.  
  
2.  Exécutez **l’Assistant Publication du package SSIS** en exécutant ISDataFeedPublishingWizard.exe à partir de C:\Program Files\Microsoft SQL Server\130\DTS\Binn ou en exécutant l’Assistant Publication de flux de données à partir du menu Démarrer.  
  
     L’Assistant crée un serveur lié à l’aide du fournisseur OLE DB pour SSIS (SSISOLEDB), puis crée une vue SQL qui se compose d’une requête sur le serveur lié. Cette requête inclut le nom du dossier, le nom du projet et le nom du package dans le catalogue SSIS.  
  
3.  Exécutez la vue SQL dans SQL Server Management Studio et examinez les résultats à partir du package SSIS. La vue envoie une requête au fournisseur OLE DB pour SSIS à l’aide du serveur lié que vous avez créé. Le fournisseur OLE DB pour SSIS exécute le package que vous avez spécifié dans la requête et retourne le jeu de résultats tabulaire.  
  
> [!IMPORTANT]  
>  Pour des instructions détaillées, voir [Procédures pas à pas : publication d’un package SSIS sous la forme d’une vue SQL](../../integration-services/data-flow/walkthrough-publish-an-ssis-package-as-a-sql-view.md).  

## <a name="configure-data-streaming-destination"></a>Configurer Data Streaming Destination
  Configurez Data Streaming Destination à l’aide de la boîte de dialogue **Éditeur avancé pour Data Streaming Destination** . Pour ouvrir cette boîte de dialogue, double-cliquez sur le composant ou cliquez avec le bouton droit sur le composant dans le concepteur de flux de données, puis cliquez sur **Modifier**.  
  
 Cette boîte de dialogue comporte trois onglets : **Propriétés du composant**, **Colonnes d’entrée** et **Propriétés d’entrée et de sortie**.  
  
## <a name="component-properties-tab"></a>Onglet Propriétés du composant  
 Cet onglet comprend les champs modifiables suivants :  
  
|Champ|Description|  
|-----------|-----------------|  
|Nom|Nom du composant Data Streaming Destination dans le package.|  
|ValidateExternalMetadata|Indique si le composant est validé à l’aide de sources de données externes au moment de la conception. Si la propriété est définie sur false, la validation avec des sources de données externes est différée jusqu’au moment de l’exécution.|  
|IDColumnName|La vue générée par l’Assistant Publication des flux de données contient cette colonne d’ID supplémentaire. La colonne d’ID est utilisée comme valeur EntityKey pour les données de sortie du flux de données lorsque les données sont consommées comme flux OData par d’autres applications.<br /><br /> Le nom par défaut de cette colonne est _ID. Vous pouvez spécifier un autre nom pour la colonne d’ID.|  
  
## <a name="input-columns-tab"></a>Onglet Colonnes d’entrée  
 Toutes les colonnes d’entrée disponibles s’affichent dans le volet supérieur de cet onglet. Sélectionnez les colonnes que vous souhaitez inclure dans la sortie de ce composant. Les colonnes sélectionnées sont affichées sous forme de liste dans le volet inférieur. Vous pouvez modifier le nom de la colonne de sortie en tapant le nouveau nom du champ **Alias de sortie** dans la liste.  
  
## <a name="input-output-properties-tab"></a>Onglet Propriétés d’entrée et de sortie  
 Cet onglet est similaire à l’onglet Colonnes d’entrée. Vous pouvez modifier les noms des colonnes de sortie dans cet onglet. Dans l’arborescence à gauche, développez **Entrée de Data Streaming Destination** , puis **Colonnes d’entrée**. Cliquez sur le nom de la colonne d’entrée et modifiez le nom de la colonne de sortie dans le volet droit.
