---
title: Boîte de dialogue Modifier les paramètres (Analysis Services-données multidimensionnelles) | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
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
  
 **Nombre maximum de tâches en parallèle**  
 Sélectionnez le nombre maximal de tâches à exécuter en parallèle par l’opération de traitement ou sélectionnez **Laisser le serveur décider** pour permettre à [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] de choisir un nombre optimal de tâches en parallèle.  
  
 **Sequential**  
 Cliquez sur cette option pour traiter les objets de manière séquentielle.  
  
 **Mode de transaction**  
 Choisissez le mode de transaction utilisé lors d'un traitement séquentiel des objets :  
  
-   **Une transaction** traite tous les objets dans la même transaction.  
  
-   Les **transactions distinctes** traitent tous les objets, y compris les objets dépendants, dans des transactions distinctes.  
  
> [!NOTE]  
>  Cette option est activée uniquement si l’option **Séquentiel** est sélectionnée.  
  
 **Option de table d’écriture différée**  
 Sélectionnez cette option utilisée pour gérer une table d'écriture différée :  
  
-   **Créer** crée une table d’écriture différée si elle n’existe pas. Une erreur se produit si une table d'écriture différée existe déjà.  
  
-   L’opération **créer crée toujours** une table d’écriture différée si elle n’existe pas, ou remplace la table d’écriture différée existante si elle existe.  
  
-   L' **utilisation existante** utilise la table d’écriture différée existante si elle existe. Une erreur se produit si une table d'écriture différée n'existe pas.  
  
 **Traiter les objets affectés**  
 Sélectionnez cette option pour inclure et traiter les objets dépendants de ceux compris dans le traitement.  
  
 **Erreurs de clé de dimension**  
 Utilisez cet onglet pour modifier les paramètres relatifs à la configuration d'erreur pour l'opération de traitement. Cet onglet contient les options suivantes :  
  
 **Utiliser la configuration d’erreur par défaut**  
 Sélectionne la configuration par défaut des erreurs pour les objets dans le traitement.  
  
 **Utiliser la configuration d'erreur personnalisée**  
 Sélectionnez cette option pour définir la configuration d'erreur pour les objets dans l'opération de traitement.  
  
 **Action de l’erreur de clé**  
 Choisissez l'une des actions suivantes qui se produit lorsqu'une nouvelle clé est détectée lors du traitement sans recherche possible :  
  
-   **Convertir en données inconnues** agrège les informations de l’enregistrement dans le membre inconnu.  
  
-   **Ignorer l’enregistrement** exclut les informations de l’enregistrement du traitement de l’objet.  
  
 **Ignorer le nombre d’erreurs**  
 Cliquez sur cette option pour ignorer les erreurs qui se produisent lors du traitement.  
  
 **Arrêter en cas d’erreur**  
 Cliquez sur cette option pour arrêter le traitement en cas d'erreurs. Cette option active les options **Nombre d'erreurs** et **Action pour l'erreur** .  
  
 **Nombre d’erreurs**  
 Tapez le nombre d'erreurs à ignorer avant l'arrêt du traitement.  
  
 **Action en cas d’erreur**  
 Choisissez l’une des actions suivantes à effectuer quand le nombre d’erreurs dépasse la valeur spécifiée dans **Nombre d’erreurs**:  
  
-   **Arrêter le traitement** met fin à l’opération de traitement.  
  
-   **Arrêter la journalisation** arrête l’enregistrement des erreurs, mais poursuit l’opération de traitement.  
  
 **Clé introuvable**  
 Spécifiez une des actions suivantes à effectuer lorsqu'une clé est introuvable pendant le traitement d'un objet :  
  
-   **Ignorer l’erreur** ignore l’erreur.  
  
-   **Signaler et continuer** signale l’erreur et poursuit l’opération de traitement.  
  
-   **Signaler et arrêter** signale l’erreur et arrête l’opération de traitement.  
  
 **Clé dupliquée**  
 Spécifiez une des actions suivantes à effectuer lorsqu'une clé dupliquée est trouvée pendant le traitement d'un objet :  
  
-   **Ignorer l’erreur** ignore l’erreur.  
  
-   **Signaler et continuer** signale l’erreur et poursuit l’opération de traitement.  
  
-   **Signaler et arrêter** signale l’erreur et arrête l’opération de traitement.  
  
 **Clé null convertie en clé inconnue**  
 Spécifiez l'une des actions suivantes à entreprendre lorsqu'une clé de membre NULL est ajoutée au membre inconnu lors du traitement d'un objet :  
  
-   **Ignorer l’erreur** ignore l’erreur.  
  
-   **Signaler et continuer** signale l’erreur et poursuit l’opération de traitement.  
  
-   **Signaler et arrêter** signale l’erreur et arrête l’opération de traitement.  
  
 **Clé null non autorisée**  
 Spécifiez l'une des actions suivantes à entreprendre lorsqu'une clé NULL est détectée mais non autorisée, lors du traitement d'un objet :  
  
-   **Ignorer l’erreur** ignore l’erreur.  
  
-   **Signaler et continuer** signale l’erreur et poursuit l’opération de traitement.  
  
-   **Signaler et arrêter** signale l’erreur et arrête l’opération de traitement.  
  
 **Chemin du journal des erreurs**  
 Tapez le chemin d'accès et le nom complets du fichier journal d'erreurs.  
  
 **Parcourir**  
 Cliquez sur ce bouton pour ouvrir la boîte de dialogue **Ouvrir** et sélectionnez le chemin complet et le nom de fichier pour le fichier journal d’erreurs.  
  
 **Traiter les objets affectés**  
 Cliquez sur cette option pour traiter les objets dépendants de ceux étant sélectionnés dans la boîte de dialogue **Traiter** .  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Boîte de dialogue traiter &#40;Analysis Services-données multidimensionnelles&#41;](process-dialog-box-analysis-services-multidimensional-data.md)  
  
  
