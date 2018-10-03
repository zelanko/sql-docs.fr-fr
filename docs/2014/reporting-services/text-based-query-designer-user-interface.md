---
title: Interface utilisateur du Concepteur de requêtes textuel | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 36805b803d52652d0b072f6124eb2f90cf9617c9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085739"
---
# <a name="text-based-query-designer-user-interface"></a>Interface utilisateur du Concepteur de requêtes textuel
  Utilisez le Concepteur de requêtes textuel pour spécifier une requête à l'aide du langage de requête pris en charge par la source de données, exécuter la requête et afficher les résultats au moment de la conception. Vous pouvez spécifier plusieurs instructions [!INCLUDE[tsql](../includes/tsql-md.md)] , une syntaxe de requête ou de commande pour les extensions pour le traitement des données personnalisées et des requêtes spécifiées en tant qu'expressions. Comme le Concepteur de requêtes textuel n'effectue pas de prétraitement de la requête et peut accepter tout type de syntaxe de requête, il s'agit de l'outil du Concepteur de requêtes par défaut pour de nombreux types de sources de données.  
  
 Le Concepteur de requêtes textuel affiche une barre d'outils et les deux volets suivants :  
  
-   **Requête** affiche le texte de la requête, le nom de table ou le nom de la procédure stockée.  
  
-   **Résultats** Affiche les résultats de l'exécution de la requête au moment de la conception.  
  
## <a name="text-based-query-designer-toolbar"></a>Barre d'outils du Concepteur de requêtes textuel  
 Le Concepteur de requêtes textuel fournit une barre d'outils unique pour tous les types de commandes. Le tableau suivant répertorie chaque bouton de la barre d'outils et décrit sa fonction.  
  
|Bouton|Description|  
|------------|-----------------|  
|**Modifier en tant que texte**|Bascule entre le Concepteur de requêtes textuel et le concepteur de requêtes graphique. Les types de sources de données ne prennent pas tous en charge les concepteurs de requêtes graphiques.|  
|**Importer**|Importe une requête existante à partir d'un fichier ou d'un rapport. Seuls les types de fichiers sql et rdl sont pris en charge. Pour plus d’informations, consultez [Datasets incorporés dans les rapports et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
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
  
 Vous pouvez utiliser toute instruction [!INCLUDE[tsql](../includes/tsql-md.md)] pour le texte de type de commande, y compris des instructions `EXEC`. La requête suivante appelle le [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] procédure stockée `uspGetEmployeeManagers` et retourne la chaîne de commande pour l’employé dont le numéro d’identification 1.  
  
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
  
 Lorsque vous entrez le nom de la table Sales.Customer, il est l’équivalent de la création du [!INCLUDE[tsql](../includes/tsql-md.md)] instruction `SELECT * FROM Sales.Customer;`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interroger des outils de conception dans le rapport concepteur SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Type de connexion SQL Server &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md)   
 [Type de connexion OLE DB &#40;SSRS&#41;](report-data/ole-db-connection-type-ssrs.md)   
 [Type de connexion ODBC &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Fichier de configuration RSReportDesigner](report-server/rsreportdesigner-configuration-file.md)  
  
  
