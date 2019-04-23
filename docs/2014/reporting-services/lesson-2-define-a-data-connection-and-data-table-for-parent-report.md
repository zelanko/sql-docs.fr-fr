---
title: 'Leçon 2 : Définir une connexion de données et la Table de données pour le rapport Parent | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6b7e6e38ca10cf23179872ddc3ff4476bc3657d
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59939855"
---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a>Leçon 2 : Définir une connexion de données et la Table de données pour le rapport Parent
  Après avoir créé un projet de site Web à l'aide du modèle de site Web ASP.NET pour Visual C#, l'étape suivante consiste à créer une connexion de données et une table de données pour le rapport parent. Dans ce didacticiel, la connexion de données doit s'établir avec la base de données AdventureWorks2008. Vous avez également la possibilité de vous connecter à la base de données AdventureWorks2012.  
  
### <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a>Pour définir une connexion de données et une table de données en ajoutant un dataset (pour le rapport parent)  
  
1.  Dans le menu **Site Web** , sélectionnez **Ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **DataSet** et cliquez sur **ajouter**. Lorsque vous y êtes invité vous devez ajouter l’élément à la **App_Code** dossier en cliquant sur **Oui**.  
  
     Ce faisant, vous ajoutez un nouveau fichier XSD **DataSet1.xsd** au projet et ouvrez le Concepteur de DataSet.  
  
3.  À partir de la fenêtre Boîte à outils, faites glisser un contrôle **[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** dans l’aire de conception. Cette opération permet de lancer l’Assistant de configuration de **TableAdapter** .  
  
4.  Sur le **choisir votre connexion de données** , cliquez sur **nouvelle connexion**.  
  
5.  Si vous avez créé une source de données dans Visual Studio pour la première fois, la page **Choisir une source de données** s’affiche. Dans la zone **Source de données** , sélectionnez **Microsoft SQL Server**.  
  
6.  Dans la boîte de dialogue **Ajouter une connexion** , effectuez les étapes suivantes :  
  
    1.  Dans le **nom du serveur** , entrez le serveur où le **AdventureWorks2008** base de données se trouve.  
  
         L’instance SQL Server Express par défaut est **(local)\sqlexpress**.  
  
    2.  Dans la section **Connexion au serveur** , sélectionnez l’option qui permet d’accéder aux données. **Utiliser l’authentification Windows** est la valeur par défaut.  
  
    3.  À partir de la **sélectionner ou entrer un nom de base de données** la liste déroulante, cliquez sur **AdventureWorks2008**.  
  
    4.  Cliquez sur **OK**, puis sur **Suivant**.  
  
7.  Si vous avez sélectionné **Utiliser l’authentification SQL Server** à l’étape 6 (b), déterminez s’il faut inclure les données sensibles dans la chaîne ou définir les informations dans votre code d’application.  
  
8.  Sur le **enregistrer la chaîne de connexion au fichier de Configuration de l’Application** page, tapez le nom de la chaîne de connexion ou acceptez la valeur par défaut **AdventureWorks2008ConnectionString**. Cliquer sur **Suivant**.  
  
9. Sur le **choisir un Type de commande** page, sélectionnez **utiliser des instructions SQL**, puis cliquez sur **suivant**.  
  
10. Sur le **Entrez une instruction SQL** , entrez la requête Transact-SQL suivante pour récupérer des données à partir de la **AdventureWorks2008** de base de données, puis cliquez sur **suivant**.  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
     Vous pouvez également créer la requête en cliquant sur **Générateur de requêtes**, puis vérifiez la requête en cliquant sur **exécuter la requête**. Si la requête ne retourne pas les données attendues, c'est peut-être que vous utilisez une version antérieure d'AdventureWorks. Pour plus d’informations sur l’installation de la **AdventureWorks2008** version d’AdventureWorks, consultez [procédure pas à pas : L’installation de la base de données AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).  
  
11. Sur le **choisir les méthodes à générer** page, veillez à décocher **créer des méthodes pour envoyer des mises à jour directement à la base de données (GenerateDBDirectMethods)**, puis cliquez sur **Terminer**.  
  
    > [!WARNING]  
    >  Veillez à désactiver la création  
  
     Vous venez de terminer la configuration de l'objet ADO.NET DataTable comme source de données pour votre rapport. Sur la page Concepteur de DataSet dans Visual Studio, vous devez voir l'objet DataTable que vous venez d'ajouter, répertoriant les colonnes spécifiées dans la requête. DataSet1 contient les données de la table Product, en fonction de la requête.  
  
12. Enregistrez le fichier.  
  
13. Pour afficher un aperçu des données, cliquez sur **aperçu des données** sur le **données** menu, puis sur **aperçu**.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de créer une connexion de données et une table de données pour le rapport parent. Vous allez à présent concevoir le rapport parent à l'aide de l'Assistant Rapport.  
  
  
