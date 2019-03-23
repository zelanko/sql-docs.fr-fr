---
title: Définissez les valeurs de paramètre après avoir déployé le projet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f5e7248868a368ee0ea956b46b63c9c8d024393b
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58379927"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>Définir des valeurs de paramètres après le déploiement du projet
  L'Assistant Déploiement vous permet de définir des valeurs de paramètre par défaut du serveur lorsque vous déployez votre projet dans le catalogue. Une fois votre projet dans le catalogue, vous pouvez utiliser l'Explorateur d'objets SQL Server Management Studio (SSMS) ou Transact-SQL pour définir les valeurs par défaut du serveur.  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>Pour définir les valeurs par défaut du serveur avec l'Explorateur d'objets SSMS :  
  
1.  Sélectionnez le projet sous le nœud **Integration Services**, puis cliquez dessus avec le bouton droit.  
  
2.  Cliquez sur **Propriétés** pour ouvrir la fenêtre de dialogue **Propriétés du projet** .  
  
3.  Ouvrez la page des paramètres en cliquant sur **Paramètres** sous **Sélectionner une page**.  
  
4.  Sélectionnez le paramètre souhaité dans la liste **Paramètres** . Remarque : Le **conteneur** colonne permet de distinguer les paramètres du projet à partir des paramètres de package.  
  
5.  Dans la colonne **Valeur** , spécifiez la valeur de paramètre du serveur par défaut souhaitée.  
  
 Pour définir les paramètres par défaut du serveur avec Transact-SQL, utilisez la procédure stockée [catalog.set_object_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database). Pour afficher les valeurs par défaut actuelles du serveur, interrogez la vue [catalog.object_parameters &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database). Pour effacer une valeur par défaut du serveur, utilisez la procédure stockée [catalog.clear_object_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database).  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40;SSIS&#41; paramètres](integration-services-ssis-package-and-project-parameters.md)  
  
  
