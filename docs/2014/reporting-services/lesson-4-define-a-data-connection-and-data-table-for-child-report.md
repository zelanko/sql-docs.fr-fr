---
title: 'Leçon 4 : Définir une connexion de données et la Table de données pour le rapport enfant | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d0aed81ff4ac2daa517bb17ddb53ebaf7eacdcbe
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53365411"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a>Leçon 4 : définir une connexion de données et une table de données pour le rapport enfant
  Après avoir créé le rapport parent, l'étape suivante consiste à créer une connexion de données et une table de données pour le rapport enfant. Dans ce didacticiel, la connexion de données doit s'établir avec la base de données AdventureWorks2008. Vous avez également la possibilité de vous connecter à la base de données AdventureWorks2012.  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a>Pour définir une connexion de données et un objet DataTable en ajoutant un DataSet (pour le rapport enfant)  
  
1.  Sur le **site Web** menu, cliquez sur **ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, cliquez sur **DataSet** puis cliquez sur **ajouter**. Lorsque vous y êtes invité, vous devez ajouter l’élément à la **App_Code** dossier en cliquant sur **Oui**.  
  
     Vous ajoutez ainsi un nouveau fichier XSD **DataSet2.xsd** au projet et ouvrez le Concepteur de DataSet.  
  
3.  À partir de la fenêtre Boîte à outils, faites glisser un contrôle **TableAdapter** dans l’aire de conception. Cette opération permet de lancer l’Assistant de configuration de **TableAdapter** .  
  
4.  Sur le **choisir votre connexion de données** , cliquez sur **nouvelle connexion**.  
  
5.  Dans la boîte de dialogue **Ajouter une connexion** , effectuez les étapes suivantes :  
  
    1.  Dans le **nom du serveur** , entrez le serveur où le **AdventureWorks2008** base de données se trouve.  
  
         L’instance SQL Server Express par défaut est **(local)\sqlexpress**.  
  
    2.  Dans la section **Connexion au serveur** , sélectionnez l’option qui permet d’accéder aux données. **Utiliser l’authentification Windows** est la valeur par défaut.  
  
    3.  À partir de la **sélectionner ou entrer un nom de base de données** la liste déroulante, cliquez sur **AdventureWorks2008**.  
  
    4.  Cliquez sur **OK**, puis sur **Suivant**.  
  
6.  Si vous avez sélectionné **Utiliser l’authentification SQL Server** à l’étape 5 (b), choisissez s’il faut inclure les données sensibles dans la chaîne ou définir les informations dans votre code d’application.  
  
7.  Sur le **enregistrer la chaîne de connexion au fichier de Configuration de l’Application** page, tapez le nom de la chaîne de connexion ou acceptez la valeur par défaut **AdventureWorks2008ConnectionString**. Cliquer sur **Suivant**.  
  
8.  Sur le **choisir un Type de commande** page, sélectionnez **utiliser des instructions SQL**, puis cliquez sur **suivant**.  
  
9. Sur le **Entrez une instruction SQL** , entrez la requête Transact-SQL suivante pour récupérer des données à partir de la **AdventureWorks2008** de base de données, puis cliquez sur **suivant**.  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
     Vous pouvez également créer la requête en cliquant sur **Générateur de requêtes**, puis vérifiez la requête en cliquant sur **exécuter la requête** bouton. Si la requête ne retourne pas les données attendues, c'est peut-être que vous utilisez une version antérieure d'AdventureWorks. Pour plus d’informations sur l’installation de la **AdventureWorks2008** version d’AdventureWorks, consultez [procédure pas à pas : L’installation de la base de données AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).  
  
10. Sur le **choisir les méthodes à générer** page, décochez la case **créer des méthodes pour envoyer des mises à jour directement à la base de données (GenerateDBDirectMethods)**, puis cliquez sur **Terminer**.  
  
     Vous avez maintenant terminé la configuration de l’objet ADO.NET [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) en tant que source de données pour votre rapport. Dans la page du Concepteur de DataSet dans Visual Studio, vous devez voir l’objet **DataTable** que vous avez ajouté, qui répertorie les colonnes spécifiées dans la requête. DataSet2 contient les données de la table PurchaseOrderDetail, en fonction de la requête.  
  
11. Enregistrez le fichier.  
  
12. Pour afficher un aperçu des données, cliquez sur **aperçu des données** sur le **données** menu, puis sur **aperçu**.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de créer une connexion de données et une table de données pour le rapport enfant. Vous allez à présent concevoir le rapport enfant à l'aide de l'Assistant Rapport.  
  
  
