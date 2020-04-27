---
title: 'Leçon 2 : définir une connexion de données et une table de données pour le rapport parent | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f02dee0c-85ad-45d4-b707-10e9e8541db9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 987e6924fe3fbffb416e4266861ae7cfede16596
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108495"
---
# <a name="lesson-2-define-a-data-connection-and-data-table-for-parent-report"></a>Leçon 2 : définir une connexion de données et une table de données pour le rapport parent
  Après avoir créé un projet de site Web à l'aide du modèle de site Web ASP.NET pour Visual C#, l'étape suivante consiste à créer une connexion de données et une table de données pour le rapport parent. Dans ce didacticiel, la connexion de données doit s'établir avec la base de données AdventureWorks2008. Vous avez également la possibilité de vous connecter à la base de données AdventureWorks2012.  
  
### <a name="to-define-a-data-connection-and-data-table-by-adding-a-dataset-for-parent-report"></a>Pour définir une connexion de données et une table de données en ajoutant un dataset (pour le rapport parent)  
  
1.  Dans le menu **Site Web** , sélectionnez **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **DataSet** , puis cliquez sur **Ajouter**. Lorsque vous y êtes invité, vous devez ajouter l’élément au dossier **App_Code** en cliquant sur **Oui**.  
  
     Ce faisant, vous ajoutez un nouveau fichier XSD **DataSet1.xsd** au projet et ouvrez le Concepteur de DataSet.  
  
3.  À partir de la fenêtre boîte à outils, faites glisser un contrôle **[TableAdapter](https://msdn.microsoft.com/library/bz9tthwx\(v=vs.100\).aspx)** vers l’aire de conception. Cette opération permet de lancer l’Assistant de configuration de **TableAdapter** .  
  
4.  Sur la page **choisir votre connexion de données** , cliquez sur **nouvelle connexion**.  
  
5.  S’il s’agit de la première fois que vous avez créé une source de données dans Visual Studio, la page **choisir la source de données** s’affiche. Dans la zone **Source de données** , sélectionnez **Microsoft SQL Server**.  
  
6.  Dans la boîte de dialogue **Ajouter une connexion** , effectuez les étapes suivantes :  
  
    1.  Dans la zone **nom du serveur** , entrez le serveur sur lequel se trouve la base de données **AdventureWorks2008** .  
  
         L’instance SQL Server Express par défaut est **(local)\sqlexpress**.  
  
    2.  Dans la section **Connexion au serveur** , sélectionnez l’option qui permet d’accéder aux données. **Utiliser l’authentification Windows** est la valeur par défaut.  
  
    3.  Dans la liste déroulante **Sélectionner ou entrer un nom de base de données** , cliquez sur **AdventureWorks2008**.  
  
    4.  Cliquez sur **OK**, puis cliquez sur **Suivant**.  
  
7.  Si vous avez sélectionné **Utiliser l’authentification SQL Server** à l’étape 6 (b), déterminez s’il faut inclure les données sensibles dans la chaîne ou définir les informations dans votre code d’application.  
  
8.  Sur la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , tapez le nom de la chaîne de connexion ou acceptez le **AdventureWorks2008ConnectionString**par défaut. Cliquez sur **Suivant**.  
  
9. Dans la page **choisir un type de commande** , sélectionnez **utiliser des instructions SQL**, puis cliquez sur **suivant**.  
  
10. Dans la page **Entrez une instruction SQL** , entrez la requête Transact-SQL suivante pour récupérer des données de la base de données **AdventureWorks2008** , puis cliquez sur **suivant**.  
  
    ```  
    SELECT ProductID, Name, ProductNumber, SafetyStockLevel, ReorderPoint FROM  Production.Product Order By ProductID  
    ```  
  
     Vous pouvez également créer la requête en cliquant sur **Générateur de requêtes**, puis vérifier la requête en cliquant sur **exécuter la requête**. Si la requête ne retourne pas les données attendues, c'est peut-être que vous utilisez une version antérieure d'AdventureWorks. Pour plus d’informations sur l’installation de la version **AdventureWorks2008** d’AdventureWorks, consultez [procédure pas à pas : installation de la base de données AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).  
  
11. Dans la page **choisir les méthodes à générer** , veillez à décocher **créer des méthodes pour envoyer des mises à jour directement à la base de données (GenerateDBDirectMethods)**, puis cliquez sur **Terminer**.  
  
    > [!WARNING]  
    >  Veillez à désactiver la création  
  
     Vous venez de terminer la configuration de l'objet ADO.NET DataTable comme source de données pour votre rapport. Sur la page Concepteur de DataSet dans Visual Studio, vous devez voir l'objet DataTable que vous venez d'ajouter, répertoriant les colonnes spécifiées dans la requête. DataSet1 contient les données de la table Product, en fonction de la requête.  
  
12. Enregistrez le fichier .  
  
13. Pour afficher un aperçu des données, cliquez sur **Aperçu** des données dans le menu **données** , puis cliquez sur **Aperçu**.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de créer une connexion de données et une table de données pour le rapport parent. Vous allez à présent concevoir le rapport parent à l'aide de l'Assistant Rapport.  
  
  
