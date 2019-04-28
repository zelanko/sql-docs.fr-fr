---
title: Configuration d’erreur (boîte de dialogue Structure d’exploration de données) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1cf11c572860815f46e6d20a0cf1a4b82399a93
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62731451"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a>Configuration d'erreur (boîte de dialogue Structure d'exploration de données) (Analysis Services - Données multidimensionnelles)
  Utilisez la page **Configuration d'erreur** de la boîte de dialogue **Propriétés de la structure d'exploration de données** de **SQL Server Management Studio** pour définir les propriétés de configuration des erreurs d'une structure d'exploration des données dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="options"></a>Options  
 **Utiliser la configuration d’erreur par défaut**  
 Sélectionne la configuration par défaut des erreurs pour les objets dans le traitement.  
  
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
  
-   **Ignorer l'erreur** ignore l'erreur  
  
-   **Signaler et continuer** signale l'erreur et poursuit le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Clé dupliquée**  
 Spécifiez une des actions suivantes à effectuer lorsqu'une clé dupliquée est trouvée pendant le traitement d'un objet :  
  
-   **Ignorer l'erreur** ignore l'erreur  
  
-   **Signaler et continuer** signale l'erreur et poursuit le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Clé NULL convertie en clé inconnue**  
 Spécifiez une des actions suivantes à effectuer lorsqu'un membre NULL est ajouté au membre inconnu pendant le traitement d'un objet :  
  
-   **Ignorer l'erreur** ignore l'erreur  
  
-   **Signaler et continuer** signale l'erreur et poursuit le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Clé NULL non autorisée**  
 Spécifiez une des actions suivantes à effectuer lorsqu'une clé NULL est trouvée, mais non autorisée, pendant le traitement d'un objet :  
  
-   **Ignorer l'erreur** ignore l'erreur  
  
-   **Signaler et continuer** signale l'erreur et poursuit le traitement.  
  
-   **Signaler et arrêter** signale l'erreur et met fin au traitement.  
  
 **Chemin d'accès du journal des erreurs**  
 Tapez le chemin d'accès et le nom complets du fichier journal d'erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue de propriétés Structure d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md)   
 [Général &#40;boîte de dialogue Structure d’exploration de données&#41; &#40;Analysis Services - Exploration de données&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)  
  
  
