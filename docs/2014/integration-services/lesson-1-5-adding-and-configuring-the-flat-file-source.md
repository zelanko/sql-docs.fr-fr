---
title: 'Étape 5 : Ajout et configuration de la source de fichier plat | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 32b95a5d156ae52394b7128b024c86b9a7e308b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62891537"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a>Étape 5 : Ajout et configuration de la source de fichier plat
  Au cours de cette tâche, vous allez ajouter et configurer une source de fichier plat à votre package. Une source de fichier plat est un composant de flux de données qui utilise des métadonnées définies par un Gestionnaire de connexions de fichiers plats pour spécifier le format et la structure des données à extraire à partir du fichier plat par un processus de transformation. La source de fichier plat peut être configurée pour extraire les données à partir d'un seul fichier plat en utilisant la définition de format de fichier fournie par le Gestionnaire de connexions de fichiers plats.  
  
 Pour ce didacticiel, vous allez configurer la source de fichier plat pour qu' `Sample Flat File Source Data` elle utilise le gestionnaire de connexions que vous avez créé précédemment.  
  
### <a name="to-add-a-flat-file-source-component"></a>Pour ajouter un composant source de fichier plat  
  
1.  Ouvrez le concepteur de **Workflow** , soit en double-cliquant sur `Extract Sample Currency Data` la tâche de workflow, soit en cliquant sur l' **onglet de workflow**.  
  
2.  Dans la **Boîte à outils SSIS**, développez **Autres sources**, puis faites glisser une **source de fichier plat** sur l’aire de conception de l’onglet **Flux de données** .  
  
3.  Dans l’aire de conception de **Workflow** , cliquez avec le bouton droit sur la **source de fichier plat**nouvellement ajoutée, cliquez sur **Renommer**, puis remplacez le nom par `Extract Sample Currency Data`.  
  
4.  Double-cliquez sur la source de fichier plat pour ouvrir la boîte de dialogue Éditeur de source de fichier plat.  
  
5.  Dans la zone **Gestionnaire de connexions de fichiers plats** , sélectionnez `Sample Flat File Source Data`.  
  
6.  Sélectionnez **Colonnes** et vérifiez si les noms des colonnes sont corrects.  
  
7.  Cliquez sur **OK**.  
  
8.  Cliquez avec le bouton droit sur la source de fichier plat, puis cliquez sur **Propriétés**.  
  
9. Dans la Fenêtre Propriétés, vérifiez que la `LocaleID` propriété est définie sur **anglais (États-Unis)**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 6 : Ajout et configuration des transformations de recherche](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Source de fichier plat](data-flow/flat-file-source.md)   
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page général&#41;](general-page-of-integration-services-designers-options.md)  
  
  
