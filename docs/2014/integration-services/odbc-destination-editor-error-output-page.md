---
title: Éditeur de destination ODBC (page sortie d’erreur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.errorhandling.f1
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 82853123767237314edac1e301723724628439d9
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965039"
---
# <a name="odbc-destination-editor-error-output-page"></a>Éditeur de destination ODBC (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de destination ODBC** pour sélectionner les options de gestion des erreurs.  
  
 Pour en savoir plus sur la destination ODBC, consultez [ODBC Destination](data-flow/odbc-destination.md).  
  
 **Pour ouvrir l'Éditeur de destination ODBC (page Sortie d'erreur)**  
  
## <a name="task-list"></a>Liste des tâches  
  
-   Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la destination ODBC.  
  
-   Sous l’onglet **Flux de données** , double-cliquez sur la destination ODBC.  
  
-   Dans l' **Éditeur de destination ODBC**, cliquez sur **Sortie d'erreur**.  
  
## <a name="options"></a>Options  
  
### <a name="inputoutput"></a>Entrée/sortie  
 Affichez le nom de la source de données.  
  
### <a name="column"></a>Colonne  
 Non utilisé.  
  
### <a name="error"></a>Erreur  
 Sélectionnez la façon dont la destination ODBC doit gérer les erreurs dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### <a name="truncation"></a>Troncation  
 Sélectionnez la façon dont la destination ODBC doit gérer la troncation dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### <a name="description"></a>Description  
 Affichez la description d'une erreur.  
  
### <a name="set-this-value-to-selected-cells"></a>Définir cette valeur sur les cellules sélectionnées  
 Sélectionnez la façon dont la destination ODBC gère l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### <a name="apply"></a>Appliquer  
 Appliquez les options de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="error-handling-options"></a>Options de gestion des erreurs  
 Vous pouvez utiliser les options suivantes pour configurer la façon dont la destination ODBC gère les erreurs et les troncations.  
  
### <a name="fail-component"></a>Composant défaillant  
 La tâche de flux de données échoue lorsqu'une erreur ou une troncation a lieu. Il s'agit du comportement par défaut.  
  
### <a name="ignore-failure"></a>Ignorer l'échec  
 L'erreur ou la troncation est ignorée.  
  
### <a name="redirect-flow"></a>Rediriger le flux  
 La ligne qui provoque l'erreur ou la troncation est dirigée vers la sortie d'erreur de la destination ODBC. Pour plus d'informations, consultez Destination ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de destination ODBC &#40;page Gestionnaire de connexions&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md)   
 [Éditeur de destination ODBC &#40;page Mappages&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md)  
  
  
