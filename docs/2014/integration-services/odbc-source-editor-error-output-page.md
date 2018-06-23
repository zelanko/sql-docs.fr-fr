---
title: Éditeur de Source ODBC (Page sortie d’erreur) | Documents Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.designer.odbcsource.errorhandling.f1
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f44e6a6ed649740034ee78ba3287d003e59ef75a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155068"
---
# <a name="odbc-source-editor-error-output-page"></a>Éditeur de source ODBC (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de la boîte de dialogue **Éditeur de source ODBC** pour sélectionner les options de gestion des erreurs.  
  
 Pour en savoir plus sur la source ODBC, consultez [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Liste des tâches  
 **Pour ouvrir l'Éditeur de source ODBC (page Sortie d'erreur)**  
  
-   Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] qui possède la source ODBC.  
  
-   Sous l’onglet **Flux de données** , double-cliquez sur la source ODBC.  
  
-   Dans l' **Éditeur de source ODBC**, cliquez sur **Sortie d'erreur**.  
  
## <a name="options"></a>Options  
  
### <a name="inputoutput"></a>Entrée/sortie  
 Affichez le nom de la source de données.  
  
### <a name="column"></a>colonne  
 Non utilisé.  
  
### <a name="error"></a>Error  
 Sélectionnez la façon dont la source ODBC doit gérer les erreurs dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### <a name="truncation"></a>Troncation  
 Sélectionnez la façon dont la source ODBC doit gérer la troncation dans un flux : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### <a name="description"></a>Description  
 Non utilisé.  
  
### <a name="set-this-value-to-selected-cells"></a>Définir cette valeur sur les cellules sélectionnées  
 Sélectionnez la façon dont la source ODBC gère l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
### <a name="apply"></a>Appliquer  
 Appliquez les options de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="error-handling-options"></a>Options de gestion des erreurs  
 Vous pouvez utiliser les options suivantes pour configurer la façon dont la source ODBC gère les erreurs et les troncations.  
  
### <a name="fail-component"></a>Composant défaillant  
 La tâche de flux de données échoue lorsqu'une erreur ou une troncation a lieu. Il s'agit du comportement par défaut.  
  
### <a name="ignore-failure"></a>Ignorer l'échec  
 L'erreur ou la troncation est ignorée.  
  
### <a name="redirect-flow"></a>Rediriger le flux  
 La ligne qui provoque l'erreur ou la troncation est dirigée vers la sortie d'erreur de la source ODBC. Pour plus d'informations, consultez [ODBC Source](data-flow/odbc-source.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source ODBC &#40;Page Gestionnaire de connexions&#41;](../../2014/integration-services/odbc-source-editor-connection-manager-page.md)   
 [Éditeur de Source ODBC &#40;Page colonnes&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md)  
  
  