---
title: Générer des scripts (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b757452c98241d10fa4c9d8b0eeba8ab73f03ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288745"
---
# <a name="generate-scripts-sql-server-management-studio"></a>Générer des scripts (SQL Server Management Studio)
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fournit deux mécanismes pour générer des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] . Vous pouvez créer des scripts pour plusieurs objets au moyen de l' **Assistant Générer et publier des scripts**. Vous pouvez également générer un script pour des objets individuels ou plusieurs objets à l'aide du menu **Script en tant que** dans l' **Explorateur d'objets**.  
  
1.  **Choisissez une méthode :**  [Assistant Générer et publier des scripts](#GenPubScriptWiz), [Menu Script en tant que de l'Explorateur d'objets](#OEScriptAsMenu)  
  
2.  **Pour utiliser le menu Script en tant que :**  [Générer un script d'un objet unique](#ScriptSingleObject), [Générer un script de deux objets à l'aide de l'Explorateur d'objets](#ScriptTwoObjectsOE), [Générer un script de deux objets à l'aide de la page Détails de l'Explorateur d'objets](#ScriptTwoObjectsOED)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Choisissez le mécanisme qui correspond le mieux à vos besoins.  
  
###  <a name="GenPubScriptWiz"></a> Assistant Générer et publier des scripts  
 Utilisez l' **Assistant Générer et publier des scripts** pour créer un script [!INCLUDE[tsql](../../includes/tsql-md.md)] pour plusieurs objets. L'Assistant génère un script de tous les objets d'une base de données, ou un sous-ensemble des objets que vous sélectionnez. L'Assistant propose de nombreuses options pour vos scripts et vous permet notamment d'inclure ou non des autorisations, un classement et des contraintes. Pour obtenir des instructions sur l'utilisation de l'Assistant, consultez [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md).  
  
###  <a name="OEScriptAsMenu"></a> Menu Script en tant que de l'Explorateur d'objets  
 Vous pouvez utiliser le menu **Script en tant que de l'Explorateur d'objets** pour générer un script d'un objet unique, de plusieurs objets ou de plusieurs instructions pour des objets uniques. Vous pouvez choisir un type de scripts parmi plusieurs ; par exemple pour créer, modifier ou supprimer l'objet. Vous pouvez enregistrer le script dans une fenêtre Éditeur de requête, dans un fichier ou dans le Presse-papiers. Le script est créé au format Unicode.  
  
##  <a name="ScriptSingleObject"></a> Pour générer un script d'un objet unique  
 **Pour générer un script d'un objet unique**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, puis développez la base de données contenant l'objet pour lequel un script doit être généré.  
  
3.  Développez la catégorie de l'objet. Par exemple, développez le nœud **Tables** ou **Vues** .  
  
4.  Cliquez avec le bouton droit sur l’objet et pointez sur **Générer un script de \<type d’objet> en tant que**. Par exemple, pointez sur **Générer un script de la table en tant que**.  
  
5.  Pointez sur le type de script, tel que **Create to** ou **Alter to**.  
  
6.  Sélectionnez l'emplacement dans lequel vous voulez enregistrer le script, tel que **Nouvelle fenêtre d'éditeur de requête** ou **Presse-papiers**.  
  
##  <a name="ScriptTwoObjectsOE"></a> Pour générer un script de deux objets à l'aide de l'Explorateur d'objets  
 **Pour générer un script de deux objets à l'aide de l'Explorateur d'objets**  
  
 Vous pouvez parfois avoir besoin d'utiliser un script avec plusieurs options permettant, par exemple, de supprimer et de créer une procédure ou bien de créer une table puis de la modifier. Les processus ci-dessous de génération de scripts pour plusieurs objets fonctionnent également si vous devez créer un script qui référence différents types d'objets, tels que les tables, les vues et les procédures stockées.  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, puis développez la base de données contenant les objets pour lequel un script doit être généré.  
  
3.  Cliquez avec le bouton droit sur le premier objet pour lequel générer un script, pointez sur **Générer un script de \<type d’objet> en tant que** puis, dans les sélections **Enregistrer sous**, choisissez **Nouvelle fenêtre d’éditeur de requête** comme destination de sortie.  
  
4.  Accédez au deuxième objet pour lequel vous voulez générer un script.  
  
5.  Cliquez avec le bouton droit sur l’objet, pointez sur **Générer un script de \<type d’objet> en tant que** puis, dans les sélections **Enregistrer sous**, choisissez **Presse-papiers** comme destination de sortie.  
  
6.  Dans la fenêtre de l'Éditeur de requête ouverte pour le premier objet, collez le script pour le deuxième objet du presse-papiers.  
  
##  <a name="ScriptTwoObjectsOED"></a> Pour générer un script de deux objets à l'aide de la page Détails de l'Explorateur d'objets  
 **Pour générer un script de deux objets à l'aide de la page Détails de l'Explorateur d'objets**  
  
 Vous pouvez utiliser le volet **Détails de l'Explorateur d'objets** pour générer un script pour plusieurs objets de la même catégorie.  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Développez **Bases de données**, puis développez la base de données contenant les objets pour lequel un script doit être généré.  
  
3.  Développez le nœud de catégorie des types d'objet pour lesquels vous voulez générer un script, tel que le nœud **Tables** .  
  
4.  Ouvrez le volet **Détails de l'Explorateur d'objets** en appuyant sur **F7**, ou en ouvrant le menu **Affichage** et en sélectionnant **Détails de l'Explorateur d'objets**.  
  
5.  Cliquez avec le bouton gauche sur l'un des objets pour lesquels vous voulez générer un script.  
  
6.  Appuyez sur Crtl + clic gauche sur le deuxième objet pour lequel vous voulez générer un script.  
  
7.  Cliquez avec le bouton droit sur l’un des objets sélectionnés et sélectionnez **Générer un script de \<type d’objet> en tant que**.  
  
  
