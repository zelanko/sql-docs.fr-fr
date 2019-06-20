---
title: Modifier la boîte de dialogue Paramètres (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.process.batchsettingsdialog.f1
ms.assetid: 0041e042-d7ce-48f9-a690-a6dc65471ff3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 43dfc1dca2e60fe2f5e467556ee36c3add1a9da3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66088249"
---
# <a name="change-settings-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Modifier les paramètres (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Modifier les paramètres** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] et [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour changer les paramètres de traitement des objets figurant dans la boîte de dialogue **Traiter** . Vous pouvez afficher la boîte de dialogue **Modifier les paramètres** en cliquant sur **Modifier les paramètres** dans la boîte de dialogue **Traiter** .  
  
> [!NOTE]  
>  Les paramètres y étant spécifiés remplacent les paramètres par défaut hérités de la base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , pour les objets répertoriés dans la boîte de dialogue **Traiter** .  
  
## <a name="options"></a>Options  
 **Options de traitement**  
 Utilisez cet onglet pour modifier les paramètres relatifs à l'ordre de traitement, à la table d'écriture différée et aux objets affectés pour le traitement. Cet onglet contient les options suivantes :  
  
 **Parallel**  
 Cliquez sur cette option pour traiter les objets en parallèle.  
  
 **Nombre maximum de tâches parallèles**  
 Sélectionnez le nombre maximal de tâches à exécuter en parallèle par l’opération de traitement ou sélectionnez **Laisser le serveur décider** pour permettre à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de choisir un nombre optimal de tâches en parallèle.  
  
 **Séquentiel**  
 Cliquez sur cette option pour traiter les objets de manière séquentielle.  
  
 **Mode de transaction**  
 Choisissez le mode de transaction utilisé lors d'un traitement séquentiel des objets :  
  
-   L'option**Une seule transaction** traite tous les objets dans la même transaction.  
  
-   L'option**Transactions séparées** traite tous les objets, notamment les objets dépendants, dans des transactions séparées.  
  
> [!NOTE]  
>  Cette option est activée uniquement si l’option **Séquentiel** est sélectionnée.  
  
 **Option de table d’écriture différée**  
 Sélectionnez cette option utilisée pour gérer une table d'écriture différée :  
  
-   L'option**Créer** crée une table d'écriture différée si elle n'existe pas. Une erreur se produit si une table d'écriture différée existe déjà.  
  
-   L'option**Toujours créer** crée une table d'écriture différée si elle n'existe pas ou elle remplace la table existante si elle existe.  
  
-   L'option**Utiliser l'existante** utilise la table d'écriture différée existante si elle existe. Une erreur se produit si une table d'écriture différée n'existe pas.  
  
 **Traiter les objets affectés**  
 Sélectionnez cette option pour inclure et traiter les objets dépendants de ceux compris dans le traitement.  
  
 **Erreurs de clé de dimension**  
 Utilisez cet onglet pour modifier les paramètres relatifs à la configuration d'erreur pour l'opération de traitement. Cet onglet contient les options suivantes :  
  
 **Utiliser la configuration d’erreur par défaut**  
 Sélectionne la configuration par défaut des erreurs pour les objets dans le traitement.  
  
 **Utiliser la configuration d’erreur personnalisés**  
 Sélectionnez cette option pour définir la configuration d'erreur pour les objets dans l'opération de traitement.  
  
 **Action pour l'erreur de clé**  
 Choisissez l'une des actions suivantes qui se produit lorsqu'une nouvelle clé est détectée lors du traitement sans recherche possible :  
  
-   L'option**Convertir en clé inconnue** agrège les informations de l'enregistrement dans le membre inconnu.  
  
-   L'option**Annuler l'enregistrement** empêche le traitement des informations de l'enregistrement, avec cet objet.  
  
 **Ignorer le nombre d’erreurs**  
 Cliquez sur cette option pour ignorer les erreurs qui se produisent lors du traitement.  
  
 **Arrêter en cas d'erreur**  
 Cliquez sur cette option pour arrêter le traitement en cas d'erreurs. Cette option active les options **Nombre d'erreurs** et **Action pour l'erreur** .  
  
 **Nombre d'erreurs**  
 Tapez le nombre d'erreurs à ignorer avant l'arrêt du traitement.  
  
 **Action pour l'erreur**  
 Choisissez l’une des actions suivantes à effectuer quand le nombre d’erreurs dépasse la valeur spécifiée dans **Nombre d’erreurs**:  
  
-   L'option**Arrêter le traitement** met un terme au traitement.  
  
-   L'option**Arrêter l'inscription dans le journal** arrête l'inscription des erreurs dans le journal mais elle continue le traitement.  
  
 **Clé introuvable**  
 Spécifiez une des actions suivantes à effectuer lorsqu'une clé est introuvable pendant le traitement d'un objet :  
  
-   L'option**Ignorer l'erreur** ignore l'erreur.  
  
-   L'option**Signaler et continuer** signale l'erreur et continue le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Clé dupliquée**  
 Spécifiez une des actions suivantes à effectuer lorsqu'une clé dupliquée est trouvée pendant le traitement d'un objet :  
  
-   L'option**Ignorer l'erreur** ignore l'erreur.  
  
-   L'option**Signaler et continuer** signale l'erreur et continue le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Clé NULL convertie en clé inconnue**  
 Spécifiez l'une des actions suivantes à entreprendre lorsqu'une clé de membre NULL est ajoutée au membre inconnu lors du traitement d'un objet :  
  
-   L'option**Ignorer l'erreur** ignore l'erreur.  
  
-   L'option**Signaler et continuer** signale l'erreur et continue le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Clé NULL non autorisée**  
 Spécifiez l'une des actions suivantes à entreprendre lorsqu'une clé NULL est détectée mais non autorisée, lors du traitement d'un objet :  
  
-   L'option**Ignorer l'erreur** ignore l'erreur.  
  
-   L'option**Signaler et continuer** signale l'erreur et continue le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Chemin d'accès du journal des erreurs**  
 Tapez le chemin d'accès et le nom complets du fichier journal d'erreurs.  
  
 **Parcourir**  
 Cliquez sur ce bouton pour ouvrir la boîte de dialogue **Ouvrir** et sélectionnez le chemin complet et le nom de fichier pour le fichier journal d’erreurs.  
  
 **Traiter les objets affectés**  
 Cliquez sur cette option pour traiter les objets dépendants de ceux étant sélectionnés dans la boîte de dialogue **Traiter** .  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Boîte de dialogue traiter &#40;Analysis Services - données multidimensionnelles&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
