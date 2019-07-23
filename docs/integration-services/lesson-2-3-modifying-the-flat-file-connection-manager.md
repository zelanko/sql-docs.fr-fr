---
title: 'Étape 3 : Modifier le gestionnaire de connexions de fichiers plats | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 1cb492b9b162c9494c4cd009fd3ad5b68427a030
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086582"
---
# <a name="lesson-2-3-modify-the-flat-file-connection-manager"></a>Leçon 2-3 : Modifier le gestionnaire de connexions de fichiers plats

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Au cours de cette tâche, vous allez modifier le gestionnaire de connexions de fichiers plats de la leçon 1. Ce gestionnaire de connexions de fichiers plats est configuré pour charger statiquement un seul fichier. Pour faire en sorte que le gestionnaire de connexions de fichiers plats charge les fichiers de manière itérative, vous devez modifier sa propriété ConnectionString de sorte à utiliser la variable définie par l’utilisateur `User::varFileName`. Celle-ci contient le chemin du fichier à charger au moment de l’exécution.  
  
En modifiant le gestionnaire de connexions de sorte à utiliser la valeur de la variable définie par l’utilisateur pour modifier la propriété ConnectionString, le gestionnaire de connexions se connecte à différents fichiers plats. Au moment de l’exécution, chaque itération du conteneur de boucles Foreach met à jour la variable `User::varFileName`. Si la variable est à son tour mise à jour, le Gestionnaire de connexions se connecte à un autre fichier plat et la tâche de flux de données traite un autre jeu de données.  
  
## <a name="configure-the-flat-file-connection-manager-to-use-a-variable"></a>Configurer le gestionnaire de connexions de fichiers plats pour utiliser une variable  
  
1.  Dans le volet **Gestionnaires de connexions** , cliquez avec le bouton droit sur **Sample Flat File Source Data**, puis sélectionnez **Propriétés**.  

2.  Dans la fenêtre **Propriétés**, vérifiez que le **PackagePath** commence par **\Package.Connections**. Si ce n’est pas le cas, dans le volet **Gestionnaires de connexions**, cliquez avec le bouton droit sur **Sample Flat File Source Data**, puis sélectionnez **Convertir en connexion de package**.
  
3.  Dans la fenêtre **Propriétés**, pour **Expressions**, sélectionnez la cellule vide, puis le bouton **(...)** .  
  
4.  Dans la boîte de dialogue **Éditeur d’expressions de la propriété**, dans la colonne **Propriété**, sélectionnez **ConnectionString**.  
  
5.  Dans la colonne **Expression**, sélectionnez le bouton **(...)** pour ouvrir la boîte de dialogue **Générateur d’expressions**.  
  
6.  Dans la boîte de dialogue **Générateur d’expressions**, développez le nœud **Variables**.  
  
7.  Faites glisser la variable **User::varFileName** dans la zone **Expression**.  
  
8.  Sélectionnez **OK** pour fermer la boîte de dialogue **Générateur d’expressions**.  
  
9.  Resélectionnez **OK** pour fermer la boîte de dialogue **Éditeur d’expressions de la propriété**.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante  
[Étape 4 : Tester le package du tutoriel de la leçon 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
  
