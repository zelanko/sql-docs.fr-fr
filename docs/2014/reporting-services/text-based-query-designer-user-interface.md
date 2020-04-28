---
title: Interface utilisateur du concepteur de requêtes textuel | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 340040a0806a87d55582356d085ab924e25b6a48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388679"
---
# <a name="text-based-query-designer-user-interface"></a>Interface utilisateur du Concepteur de requêtes textuel
  Utilisez le Concepteur de requêtes textuel pour spécifier une requête à l'aide du langage de requête pris en charge par la source de données, exécuter la requête et afficher les résultats au moment de la conception. Vous pouvez spécifier plusieurs instructions [!INCLUDE[tsql](../includes/tsql-md.md)] , une syntaxe de requête ou de commande pour les extensions pour le traitement des données personnalisées et des requêtes spécifiées en tant qu'expressions. Comme le Concepteur de requêtes textuel n'effectue pas de prétraitement de la requête et peut accepter tout type de syntaxe de requête, il s'agit de l'outil du Concepteur de requêtes par défaut pour de nombreux types de sources de données.

 Le Concepteur de requêtes textuel affiche une barre d'outils et les deux volets suivants :

-   **Requête** Affiche le texte de la requête, le nom de la table ou le nom de la procédure stockée.

-   **Résultats** Affiche les résultats de l'exécution de la requête au moment de la conception.

## <a name="text-based-query-designer-toolbar"></a>Barre d'outils du Concepteur de requêtes textuel
 Le Concepteur de requêtes textuel fournit une barre d'outils unique pour tous les types de commandes. Le tableau suivant répertorie chaque bouton de la barre d'outils et décrit sa fonction.

|Bouton|Description|
|------------|-----------------|
|**Modifier en tant que texte**|Bascule entre le Concepteur de requêtes textuel et le concepteur de requêtes graphique. Les types de sources de données ne prennent pas tous en charge les concepteurs de requêtes graphiques.|
|**Importer**|Importe une requête existante à partir d'un fichier ou d'un rapport. Seuls les types de fichiers sql et rdl sont pris en charge. Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|
|![Exécuter la requête](../analysis-services/media/rsqdicon-run.gif "Exécuter la requête")|Exécute la requête et affiche le jeu de résultats dans le volet Résultats.|
|**Type de commande**|Sélectionnez **Text**, **StoredProcedure**ou **TableDirect**. Si une procédure stockée comporte des paramètres, la boîte de dialogue **Définir les paramètres de la requête** s'affiche lorsque vous cliquez sur **Exécuter** dans la barre d'outils, et vous pouvez spécifier les valeurs souhaitées. Notez que si une procédure stockée retourne plusieurs jeux de résultats, seul le premier jeu de résultats est utilisé pour remplir le jeu de données.<br /><br /> La prise en charge du type de commande varie en fonction du type de source de données. Par exemple, seuls OLE DB et ODBC prennent en charge **TableDirect**.|

### <a name="command-type-text"></a>Texte de type de commande
 Lorsque vous créez un dataset [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le Concepteur de rapports affiche par défaut le concepteur de requêtes graphique. Pour basculer vers le concepteur de requêtes textuel, cliquez sur le bouton bascule **Modifier en tant que texte** dans la barre d’outils. Le concepteur de requêtes textuel présente deux volets : Requête et Résultats. L'illustration suivante présente chaque volet.

 ![Concepteur de requêtes générique pour les requêtes de données relationnelles](../analysis-services/media/rsqd-dsaw-sql-generic.gif "Concepteur de requêtes générique pour les requêtes de données relationnelles")

 Le tableau ci-dessous décrit la fonction de chaque volet.

|Volet|Fonction|
|----------|--------------|
|Requête|Affiche le texte de la requête [!INCLUDE[tsql](../includes/tsql-md.md)] . Ce volet permet d'écrire ou de modifier une requête [!INCLUDE[tsql](../includes/tsql-md.md)] .|
|Résultats|Affiche les résultats de la requête. Pour exécuter la requête, cliquez avec le bouton droit dans un volet et cliquez sur **Exécuter**, ou cliquez sur le bouton **Exécuter** dans la barre d’outils.|

#### <a name="example"></a>Exemple
 La requête suivante retourne la liste des noms depuis la table `Contact` de la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)].

```
SELECT LastName FROM Person.Person;
```

 Vous pouvez utiliser toute instruction [!INCLUDE[tsql](../includes/tsql-md.md)] pour le texte de type de commande, y compris des instructions `EXEC`. La requête suivante appelle la [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] procédure `uspGetEmployeeManagers` stockée et retourne la chaîne de commande de l’employé portant le numéro d’identification 1.

```
EXEC uspGetEmployeeManagers 1;
```

 Lorsque vous cliquez sur **Exécuter** dans la barre d'outils, la commande du volet **Requête** s'exécute et les résultats s'affichent dans le volet **Résultat** .

### <a name="command-type-storedprocedure"></a>Type de commande StoredProcedure
 Quand vous sélectionnez le **Type de commande StoredProcedure**, le concepteur de requêtes textuel présente deux volets : Requête et Résultats. Entrez le nom de la procédure stockée dans le volet Requête, puis cliquez sur **Exécuter** dans la barre d'outils. La boîte de dialogue Définir les paramètres de la requête s'affiche. Entrez les valeurs des paramètres de la procédure stockée. Pour chaque paramètre de procédure stockée, un paramètre de rapport est créé.

#### <a name="example"></a>Exemple
 La requête suivante appelle la procédure stockée `uspGetEmployeeManagers` de [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]. Vous devez entrer une valeur pour le paramètre du numéro d'identification de l'employé lorsque vous exécutez la requête.

```
uspGetEmployeeManagers;
```

### <a name="command-type-tabledirect"></a>Type de commande TableDirect
 Quand vous sélectionnez le **Type de commande TableDirect**, le concepteur de requêtes textuel présente deux volets : Requête et Résultats. Lorsque vous entrez une table et cliquez sur le bouton **Exécuter** , toutes les colonnes pour cette table sont retournées.

#### <a name="example"></a>Exemple
 La requête suivante retourne un jeu de résultats pour tous les clients de la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)].

 `Sales.Customer`

 Lorsque vous entrez le nom de la table Sales. Customer, cela revient à créer [!INCLUDE[tsql](../includes/tsql-md.md)] l' `SELECT * FROM Sales.Customer;`instruction.

## <a name="see-also"></a>Voir aussi
 [Outils de conception de requête dans Concepteur de rapports SQL Server Data Tools &#40;ssrs&#41;](report-data/query-design-tools-ssrs.md) [des datasets incorporés et des datasets partagés &#40;générateur de rapports et SSRS](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)&#41;SQL Server [type de connexion &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) [OLE DB type de connexion &#40;SSRS&#41;](report-data/ole-db-connection-type-ssrs.md) [type de connexion ODBC &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md) [rapport Datasets incorporés et des datasets partagés &#40;générateur de rapports et SSRS&#41;fichier de](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [configuration RSReportDesigner](report-server/rsreportdesigner-configuration-file.md)


