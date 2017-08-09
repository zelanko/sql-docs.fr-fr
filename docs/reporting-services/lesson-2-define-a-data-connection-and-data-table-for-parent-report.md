---
title: "Leçon 2 : Définir une connexion de données et la Table de données pour le rapport Parent | Documents Microsoft"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: adc2cc7d329586bae6fb85edb08d71fe51aaaef8
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a>Leçon 2 : définir une connexion de données et une table de données pour le rapport parent
Après avoir créé un projet de site Web à l'aide du modèle de site Web ASP.NET pour Visual C#, l'étape suivante consiste à créer une connexion de données et une table de données pour le rapport parent. Dans ce didacticiel, la connexion de données doit s’établir avec la base de données AdventureWorks2014.  
  
## <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a>Pour définir une connexion de données et une table de données en ajoutant un dataset (pour le rapport parent)  
  
1.  Dans le menu **Site Web** , sélectionnez **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **DataSet** , puis sélectionnez **Ajouter**. Quand vous y êtes invité, vous devez ajouter l’élément au dossier **App_Code** en sélectionnant **Oui**.  
  
    Ce faisant, vous ajoutez un nouveau fichier XSD **DataSet1.xsd** au projet et ouvrez le Concepteur de DataSet.  
  
3.  À partir de la fenêtre Boîte à outils, faites glisser un contrôle **[TableAdapter](http://msdn.microsoft.com/library/bz9tthwx.aspx)** dans l’aire de conception. Cette opération permet de lancer l’Assistant de configuration de **TableAdapter** .  
  
4.  Dans la page **Choisir votre connexion de données** , sélectionnez **Nouvelle connexion**.  
  
5.  S’il s’agit de la première fois que vous avez créé une source de données dans Visual Studio, vous verrez s’afficher la page **Choisir une source de données** . Dans la zone **Source de données** , sélectionnez **Microsoft SQL Server**.  
  
6.  Dans la boîte de dialogue **Ajouter une connexion** , effectuez les étapes suivantes :  
  
    1.  Dans la zone **Nom du serveur** , entrez le serveur sur lequel se trouve la base de données **AdventureWorks2014** .  
  
        L’instance SQL Server Express par défaut est **(local)\sqlexpress**.  
  
    2.  Dans la section **Connexion au serveur** , sélectionnez l’option qui permet d’accéder aux données. **Utiliser l’authentification Windows** est la valeur par défaut.  
  
    3.  Dans la zone déroulante **Sélectionner ou entrer un nom de base de données** , sélectionnez **AdventureWorks2014**.  
  
    4.  Sélectionnez **OK**, puis **Suivant**.  
  
7.  Si vous avez sélectionné **Utiliser l’authentification SQL Server** à l’étape 6 (b), déterminez s’il faut inclure les données sensibles dans la chaîne ou définir les informations dans votre code d’application.  
  
8.  Dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , tapez le nom de la chaîne de connexion ou acceptez **AdventureWorks2014ConnectionString**par défaut. Sélectionnez **Suivant**.  
  
9. Dans la page **Choisissez un type de commande** , sélectionnez **Utiliser des instructions SQL**, puis sélectionnez **Suivant**.  
  
10. Dans la page **Entrez une instruction SQL** , entrez la requête Transact-SQL ci-après pour récupérer des données de la base de données **AdventureWorks2014** , puis sélectionnez **Suivant**.  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
    Vous pouvez également créer la requête en sélectionnant **Générateur de requêtes**, puis vérifier la requête en sélectionnant **Exécuter la requête**. Si la requête ne retourne pas les données attendues, c'est peut-être que vous utilisez une version antérieure d'AdventureWorks. Pour plus d’informations sur la façon d’obtenir l’exemple de base de données exemple **AdventureWorks2014** , consultez [Microsoft SQL Server Database Product Samples](http://msftdbprodsamples.codeplex.com/)(Exemples de produits de bases de données Microsoft SQL Server).  
  
11. Dans la page **Choisir les méthodes à générer** , veillez à décocher **Créer des méthodes pour envoyer directement des mises à jour à la base de données (GenerateDBDirectMethods)**, puis sélectionnez **Terminer**.  
  
    > [!WARNING]  
    > Veillez à décocher **Créer des méthodes pour envoyer directement des mises à jour à la base de données (GenerateDBDirectMethods)**.  
  
    Vous venez de terminer la configuration de l'objet ADO.NET DataTable comme source de données pour votre rapport. Sur la page Concepteur de DataSet dans Visual Studio, vous devez voir l'objet DataTable que vous venez d'ajouter, répertoriant les colonnes spécifiées dans la requête. DataSet1 contient les données de la table Product, en fonction de la requête.  
  
12. Enregistrez le fichier.  
  
13. Pour afficher un aperçu des données, sélectionnez **Aperçu des données** dans le menu **Données** , puis sélectionnez **Aperçu**.  
  
## <a name="next-task"></a>Tâche suivante  
Vous venez de créer une connexion de données et une table de données pour le rapport parent. Vous allez à présent concevoir le rapport parent à l'aide de l'Assistant Rapport. Consultez [Leçon 3 : Concevoir le rapport parent à l’aide de l’Assistant Rapport](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md).  
  


