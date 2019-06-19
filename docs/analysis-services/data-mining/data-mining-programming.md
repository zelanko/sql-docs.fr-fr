---
title: Analysis Services de programmation d’exploration de données | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1b4068d012b64cb4fc5352ed11c8576a38d6d6c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65450118"
---
# <a name="data-mining-programming"></a>Programmation de l'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

  Si vous estimez que les outils et composants intégrés dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne répondent pas à vos besoins, vous pouvez étendre la puissance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en codant vos propres extensions. Dans cette optique, deux options sont à votre disposition :  
  
-   **XMLA**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge XML for Analysis (XMLA) comme protocole de communication avec les applications clientes. Des commandes supplémentaires qui étendent la spécification XML for Analysis sont prises en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Dans la mesure où [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise XMLA pour la définition, la manipulation et le contrôle de données, vous pouvez créer des structures et des modèles d'exploration de données à l'aide des outils visuels fournis par [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], puis étendre les objets d'exploration de données que vous avez créés en utilisant des scripts DMX (Data Mining Extensions) et ASSL (Analysis Services Scripting Language).  
  
     Vous pouvez créer et modifier des objets d'exploration de données entièrement dans des scripts XMLA et exécuter par programme des requêtes de prédiction sur les modèles à partir de vos propres applications.  
  
-   **Analysis Management Objects (AMO)**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] propose également une infrastructure complète permettant aux fournisseurs d'exploration de données tiers d'intégrer les objets d'exploration de données dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     Créez des structures et des modèles d'exploration de données à l'aide d'AMO. Consultez les exemples suivants dans CodePlex :  
  
    -   Navigateur d'indicateur de performance clé (AMO)  
  
         Se connecte à l'instance SSAS spécifiée et répertorie tous les objets serveur et leurs propriétés, notamment la structure d'exploration de données et les modèles d'exploration de données.  
  
    -   Exemple AMO simple  
  
         L'exemple AS simple couvre l'accès par programme à la plupart des objets principaux et illustre la navigation dans les métadonnées et l'accès aux valeurs des objets.  
  
         L'exemple illustre également la création et le traitement d'une structure et d'un modèle d'exploration de données, et la navigation dans un modèle d'exploration de données existant.  
  
-   **DMX**  
  
     Vous pouvez utiliser DMX pour encapsuler des instructions de commande, des requêtes de prédiction et des requêtes de métadonnées, et retourner les résultats dans un format tabulaire, si vous avez créé une connexion à un serveur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [OLE DB pour l’exploration de données](data-mining-programming-ole-db.md)  
 Décrit les ajouts possibles à la spécification de manière à prendre en charge l'exploration de données et les données multidimensionnelles : nouveaux ensembles de lignes et nouvelles colonnes pour les schémas, langage DMX (Data Mining Extension) pour la création et la gestion des structures d'exploration de données.  
  
## <a name="related-reference"></a>Référence connexe  
 [Développement avec ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 Introduit les clients et serveur de programmation d’objets ADOMD.NET.  
  
 [Développement avec AMO &#40;Analysis Management Objects&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 Présente la bibliothèque de programmation AMO.  
  
 [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)  
 Présente XML for Analysis (XMLA) et ses extensions.  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation du développeur Analysis Services](../analysis-services-developer-documentation.md)   
 [Informations de référence sur le langage DMX &#40;Data Mining Extensions&#41;](../../dmx/data-mining-extensions-dmx-reference.md)  
  
  
