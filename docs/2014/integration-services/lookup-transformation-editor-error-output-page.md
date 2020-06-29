---
title: Éditeur de transformation de recherche (page sortie d’erreur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d83ceee2756e217271663a768bcb6be70983dc0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440236"
---
# <a name="lookup-transformation-editor-error-output-page"></a>Éditeur de transformation de recherche (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de transformation de recherche** pour définir les options de gestion des erreurs.  
  
 Pour en savoir plus sur la transformation de recherche, consultez [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Entrée/sortie**  
 Affichez le nom de l'entrée.  
  
 **Colonne**  
 Non utilisé.  
  
 **Error**  
 Spécifiez le type d'erreur devant se produire lors de la gestion des lignes sans entrées correspondantes dans le dataset de référence :  
  
-   ignorer l'échec et diriger les lignes vers une sortie ;  
  
-   rediriger les lignes vers une sortie d'erreur ;  
  
-   faire échouer le composant.  
  
 Cette option n'est pas disponible lorsque vous sélectionnez **Rediriger les lignes vers la sortie sans correspondance** dans la liste **Spécifier comment gérer les lignes sans entrées correspondantes** . Cette liste se trouve dans la page **Général** de la boîte de dialogue **Éditeur de transformation de recherche** .  
  
 **Rubriques connexes :** [Gestion des erreurs dans les données](data-flow/error-handling-in-data.md)  
  
 **Troncation**  
 Spécifiez ce qui doit se passer lorsqu'une troncation de données a lieu :  
  
-   ignorer l'erreur ;  
  
-   rediriger la ligne ;  
  
-   faire échouer le composant.  
  
 **Description**  
 Affichez la description de l'opération.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Indiquez ce qui doit se produire pour toutes les cellules sélectionnées lorsqu'une erreur ou une troncation a lieu :  
  
-   ignorer l'erreur ;  
  
-   rediriger la ligne ;  
  
-   faire échouer le composant.  
  
 **appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
