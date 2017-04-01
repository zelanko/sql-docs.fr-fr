---
title: "Convertir en mod&#232;le de d&#233;ploiement de package, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.bids.converttolegacydeployment.f1"
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Convertir en mod&#232;le de d&#233;ploiement de package, bo&#238;te de dialogue
  La commande **Convertir en modèle de déploiement de package** vous permet de convertir un package en modèle de déploiement de package après avoir vérifié la compatibilité du projet et de chaque package du projet avec ce modèle. Si un package utilise des fonctionnalités propres au modèle de déploiement de projet, par exemple des paramètres spécifiques, le package ne peut pas être converti.  
  
## Liste des tâches  
 La conversion d'un package en modèle de déploiement de package requiert deux étapes.  
  
1.  Quand vous sélectionnez la commande **Convertir en modèle de déploiement de package** dans le menu **Projet**, le projet et les packages individuels sont examinés dans le but de garantir leur compatibilité avec ce modèle. Les résultats s’affichent dans le tableau **Résultats**.  
  
     Si le projet ou un package ne réussit pas le test de compatibilité, cliquez sur **Échec** dans la colonne **Résultat** pour obtenir des informations supplémentaires. Cliquez sur **Enregistrer le rapport** pour enregistrer une copie de ces informations dans un fichier texte.  
  
2.  Si le projet et tous les packages réussissent le test de compatibilité, cliquez sur **OK** pour convertir le package.  
  
> **REMARQUE :** Pour convertir un projet en modèle de déploiement de projet, utilisez **l’Assistant Conversion de projet Integration Services**. Pour plus d’informations, consultez [Assistant Conversion de projet Integration Services](https://msdn.microsoft.com/library/hh213290.aspx).  
  
## Voir aussi  
 [Déploiement de packages hérités &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md)   
 [Assistant Conversion de projet Integration Services](../../integration-services/packages/integration-services-project-conversion-wizard.md)  
  
  