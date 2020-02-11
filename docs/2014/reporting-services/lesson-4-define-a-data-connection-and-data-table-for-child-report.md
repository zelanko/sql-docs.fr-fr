---
title: 'Leçon 4 : définir une connexion de données et une table de données pour le rapport enfant | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1008202519f1d9bcbf48dfdc4cd4ef3a3cbbe20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108464"
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a>Leçon 4 : définir une connexion de données et une table de données pour le rapport enfant
  Après avoir créé le rapport parent, l'étape suivante consiste à créer une connexion de données et une table de données pour le rapport enfant. Dans ce didacticiel, la connexion de données doit s'établir avec la base de données AdventureWorks2008. Vous avez également la possibilité de vous connecter à la base de données AdventureWorks2012.  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a>Pour définir une connexion de données et un objet DataTable en ajoutant un DataSet (pour le rapport enfant)  
  
1.  Dans le menu **site Web** , cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , cliquez sur **DataSet** , puis sur **Ajouter**. Lorsque vous y êtes invité, vous devez ajouter l’élément au dossier **App_Code** en cliquant sur **Oui**.  
  
     Vous ajoutez ainsi un nouveau fichier XSD **DataSet2.xsd** au projet et ouvrez le Concepteur de DataSet.  
  
3.  À partir de la fenêtre Boîte à outils, faites glisser un contrôle **TableAdapter** dans l’aire de conception. Cette opération permet de lancer l’Assistant de configuration de **TableAdapter** .  
  
4.  Sur la page **choisir votre connexion de données** , cliquez sur **nouvelle connexion**.  
  
5.  Dans la boîte de dialogue **Ajouter une connexion** , effectuez les étapes suivantes :  
  
    1.  Dans la zone **nom du serveur** , entrez le serveur sur lequel se trouve la base de données **AdventureWorks2008** .  
  
         L’instance SQL Server Express par défaut est **(local)\sqlexpress**.  
  
    2.  Dans la section **Connexion au serveur** , sélectionnez l’option qui permet d’accéder aux données. **Utiliser l’authentification Windows** est la valeur par défaut.  
  
    3.  Dans la liste déroulante **Sélectionner ou entrer un nom de base de données** , cliquez sur **AdventureWorks2008**.  
  
    4.  Cliquez sur **OK**, puis cliquez sur **Suivant**.  
  
6.  Si vous avez sélectionné **Utiliser l’authentification SQL Server** à l’étape 5 (b), choisissez s’il faut inclure les données sensibles dans la chaîne ou définir les informations dans votre code d’application.  
  
7.  Sur la page **enregistrer la chaîne de connexion dans le fichier de configuration de l’application** , tapez le nom de la chaîne de connexion ou acceptez le **AdventureWorks2008ConnectionString**par défaut. Cliquez sur **Suivant**.  
  
8.  Dans la page **choisir un type de commande** , sélectionnez **utiliser des instructions SQL**, puis cliquez sur **suivant**.  
  
9. Dans la page **Entrez une instruction SQL** , entrez la requête Transact-SQL suivante pour récupérer des données de la base de données **AdventureWorks2008** , puis cliquez sur **suivant**.  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
     Vous pouvez également créer la requête en cliquant sur **Générateur de requêtes**, puis vérifier la requête en cliquant sur le bouton **exécuter la requête** . Si la requête ne retourne pas les données attendues, c'est peut-être que vous utilisez une version antérieure d'AdventureWorks. Pour plus d’informations sur l’installation de la version **AdventureWorks2008** d’AdventureWorks, consultez [procédure pas à pas : installation de la base de données AdventureWorks](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx).  
  
10. Dans la page **choisir les méthodes à générer** , décochez **créer des méthodes pour envoyer des mises à jour directement à la base de données (GenerateDBDirectMethods)**, puis cliquez sur **Terminer**.  
  
     Vous avez maintenant terminé la configuration du [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) ADO.net comme source de données pour votre rapport. Dans la page du Concepteur de DataSet dans Visual Studio, vous devez voir l’objet **DataTable** que vous avez ajouté, qui répertorie les colonnes spécifiées dans la requête. DataSet2 contient les données de la table PurchaseOrderDetail, en fonction de la requête.  
  
11. Enregistrez le fichier .  
  
12. Pour afficher un aperçu des données, cliquez sur **Aperçu** des données dans le menu **données** , puis cliquez sur **Aperçu**.  
  
## <a name="next-task"></a>Tâche suivante  
 Vous venez de créer une connexion de données et une table de données pour le rapport enfant. Vous allez à présent concevoir le rapport enfant à l'aide de l'Assistant Rapport.  
  
  
