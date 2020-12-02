---
description: 'Leçon 1-3 : Ajouter et configurer un gestionnaire de connexions OLE DB'
title: 'Étape 3 : Ajouter et configurer un gestionnaire de connexions OLE DB | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33eeb6e462c096505fc4fbd1088e7f5b36b37618
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88449676"
---
# <a name="lesson-1-3-add-and-configure-an-ole-db-connection-manager"></a>Leçon 1-3 : Ajouter et configurer un gestionnaire de connexions OLE DB

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Après avoir ajouté un gestionnaire de connexions de fichiers plats pour la connexion à la source de données, vous ajoutez un gestionnaire de connexions OLE DB pour la connexion à la destination de données. Un Gestionnaire de connexions OLE DB permet à un package d’extraire ou de charger des données dans une source de données compatible OLE DB. À l’aide d’un gestionnaire de connexions OLE DB, vous pouvez spécifier le serveur, la méthode d’authentification et la base de données par défaut pour la connexion.  
  
Au cours de cette tâche, vous allez créer un gestionnaire de connexions OLE DB qui utilise l’authentification Windows pour la connexion à l’instance locale d’**AdventureWorksDW2012**. Ce gestionnaire de connexions OLE DB est également référencé par d’autres composants que vous allez créer ultérieurement en suivant ce tutoriel, comme la transformation de recherche et la destination OLE DB.  
  
## <a name="add-and-configure-an-ole-db-connection-manager"></a>Ajouter et configurer un gestionnaire de connexions OLE DB

1. Dans le volet **Explorateur de solutions**, cliquez avec le bouton droit sur **Gestionnaires de connexions**, puis sélectionnez **Nouveau gestionnaire de connexions**.

1. Dans la boîte de dialogue **Ajouter un gestionnaire de connexions SSIS**, sélectionnez **OLEDB**, puis **Ajouter**.
    
2. Dans la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**, sélectionnez **Nouveau**.  
  
3. Dans la zone **Nom du serveur**, entrez **localhost**.  
  
    Lorsque vous spécifiez « localhost » comme nom de serveur, le gestionnaire de connexions se connecte à l'instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l'ordinateur local. Pour utiliser une instance distante de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], remplacez « localhost » par le nom du serveur auquel vous souhaitez établir la connexion.  
  
4. Dans le groupe **Connexion au serveur** , vérifiez que l’option **Utiliser l’authentification Windows** est sélectionnée.  
  
5. Dans le groupe **Se connecter à une base de données** , dans la zone **Sélectionner ou entrer un nom de base de données** , tapez ou sélectionnez **AdventureWorksDW2012**.  
  
6. Sélectionnez **Tester la connexion** pour vérifier si les paramètres de connexion que vous avez spécifiés sont valides.  
  
7. Sélectionnez **OK**.  
  
8. Sélectionnez **OK**.  
  
9. Dans le volet **Gestionnaires de connexions**, vérifiez que **localhost.AdventureWorksDW2012** est sélectionné.  
  

## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 4 : Ajouter une tâche de flux de données au package](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a>Voir aussi  
[Gestionnaire de connexions OLE DB](../integration-services/connection-manager/ole-db-connection-manager.md)  
  
