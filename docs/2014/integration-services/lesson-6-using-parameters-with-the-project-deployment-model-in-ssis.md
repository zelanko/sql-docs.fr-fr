---
title: 'Leçon 6 : Utilisation de paramètres avec le modèle de déploiement de projet | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d559defe1dd08f26077738cdd0aea219e8f7554b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62890544"
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model"></a>Leçon 6 : Utilisation des paramètres dans le modèle de déploiement de projet
  SQL Server 2012 introduit un nouveau modèle de déploiement qui permet de déployer vos projets sur le serveur Integration Services. Le serveur Integration Services vous permet de gérer et d'exécuter les packages, et de configurer leurs valeurs d'exécution.  
  
 Dans cette leçon, vous allez modifier le package que vous avez créé dans [leçon 5 : Ajout de Configurations de Package pour le modèle de déploiement de Package](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) à utiliser le modèle de déploiement de projet. Vous remplacerez la valeur de configuration par un paramètre pour spécifier l'emplacement des exemples de données. Vous pouvez également copier le package final de la leçon 5 inclus dans le didacticiel.  
  
 À l'aide de l'Assistant Configuration de projet Integration Services, vous convertirez le projet en modèle de déploiement de projet, et vous utiliserez un paramètre au lieu d'une valeur de configuration pour définir la propriété Directory. Cette leçon couvre partiellement les étapes que vous suivriez pour convertir les packages SSIS existants en nouveau modèle de déploiement de projet.  
  
 Quand vous réexécutez le package, le service Integration Services utilise le paramètre pour donner sa valeur à la variable, qui à son tour met à jour la propriété Répertoire. Ainsi, le package itère dans les fichiers du nouveau dossier de données spécifié par la valeur du paramètre, et non du dossier défini dans le fichier de configuration du package.  
  
> [!IMPORTANT]  
>  Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d’informations sur l’installation et le déploiement de **AdventureWorksDW2012**, consultez [Considérations relatives à l’installation d’exemples de bases de données et d’exemples de code SQL Server](https://technet.microsoft.com/library/ms161556%28v=sql.105%29).  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Cette leçon contient les tâches suivantes :  
  
1.  [Étape 1 : Copie du Package de la leçon 5](lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Étape 2 : Convertir le projet dans le modèle de déploiement de projet](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Étape 3 : Test du Package de la leçon 6](lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Étape 4 : Déploiement du Package de la leçon 6](lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Démarrer la leçon  
 [Étape 1 : Copie du Package de la leçon 5](lesson-6-1-copying-the-lesson-5-package.md)  
  
  
