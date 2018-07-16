---
title: Éditeur de Transformation de recherche (Page sortie d’erreur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
caps.latest.revision: 13
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bfae0d88fe226b0c937ccdbbe36209ec2cc4c58e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227699"
---
# <a name="lookup-transformation-editor-error-output-page"></a>Éditeur de transformation de recherche (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de transformation de recherche** pour définir les options de gestion des erreurs.  
  
 Pour en savoir plus sur la transformation de recherche, consultez [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Options  
 **Entrée/sortie**  
 Affichez le nom de l'entrée.  
  
 **Colonne**  
 Non utilisé.  
  
 **Erreur**  
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
  
-   ignorer l'erreur ;  
  
-   rediriger la ligne ;  
  
-   faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
