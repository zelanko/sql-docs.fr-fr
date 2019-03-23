---
title: Référence de l’interface utilisateur de la boîte de dialogue Suggérer les types de colonnes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.suggestdatatypes.f1
ms.assetid: 8d5652e0-cf57-483f-828b-10f00c08418b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aba9a971b703a3344fc209c1c01943f10c76d767
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383059"
---
# <a name="suggest-column-types-dialog-box-ui-reference"></a>Référence de l'interface utilisateur de la boîte de dialogue Suggérer les types de colonnes
  Utilisez la boîte de dialogue **Suggérer les types de colonnes** pour identifier le type de données et la longueur des colonnes dans un gestionnaire de connexions de fichiers plats en se basant sur un échantillonnage du contenu du fichier.  
  
 Pour en savoir plus sur les types de données utilisés par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Types de données d’Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="options"></a>Options  
 **Nombre de lignes**  
 Tapez ou sélectionnez le nombre de lignes de l'échantillon utilisées par l'algorithme.  
  
 **Suggérer le plus petit type de données integer**  
 Désactivez cette case à cocher pour ignorer l'évaluation. Si elle est activée, détermine le plus petit type de données integer possible pour les colonnes contenant des données numériques entières.  
  
 **Suggérer le plus petit type de données real**  
 Désactivez cette case à cocher pour ignorer l'évaluation. Si elle est activée, détermine si les colonnes contenant des données numériques réelles peuvent utiliser le plus petit type de données real, DT_R4.  
  
 **Identifier les colonnes booléennes en utilisant les valeurs suivantes**  
 Tapez les deux valeurs à utiliser en tant que valeurs booléennes True et False. Ces valeurs doivent être séparées par une virgule, la première correspondant à la valeur True.  
  
 **Remplir les colonnes de la chaîne**  
 Activez cette case à cocher pour autoriser le remplissage de la chaîne.  
  
 **Pourcentage de remplissage**  
 Tapez ou sélectionnez le pourcentage des longueurs de colonnes à ajouter à la longueur des colonnes pour les données de type character. Ce pourcentage doit être un nombre entier.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../integration-services-error-and-message-reference.md)   
 [Gestionnaire de connexions de fichiers plats](file-connection-manager.md)  
  
  
