---
title: Types de descripteurs Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], types
ms.assetid: ec20e446-e540-41ad-8559-d9c0a5b8358f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a6c7b55194eb61c1a909ced2296e4ad2050b674
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304890"
---
# <a name="types-of-descriptors"></a>Types de descripteurs
Un descripteur est utilisé pour décrire l’un des éléments suivants :  
  
-   Un ensemble de paramètres nuls ou plus. Un descripteur de paramètre peut être utilisé pour décrire :  
  
    -   Le *tampon de paramètre d’application,* qui contient soit les arguments dynamiques d’entrée tels qu’établis par l’application, soit les arguments dynamiques de sortie après l’exécution d’une déclaration **CALL** de SQL.  
  
    -   Le *paramètre de mise en œuvre tampon*. Pour les arguments dynamiques d’entrée, cela contient les mêmes arguments que le tampon de paramètre d’application, après toute conversion de données que l’application peut spécifier. Pour les arguments dynamiques de sortie, cela contient les arguments retournés, avant toute conversion de données que l’application peut spécifier.  
  
     Pour les arguments dynamiques d’entrée, l’application doit fonctionner sur un descripteur de paramètres d’application avant d’exécuter toute déclaration SQL qui contient des marqueurs de paramètres dynamiques. Pour les arguments dynamiques d’entrée et de sortie, l’application peut spécifier différents types de données de ceux du descripteur du paramètre de mise en œuvre pour réaliser la conversion des données.  
  
-   Une seule série de données de base de données. Un descripteur de ligne peut être utilisé pour décrire :  
  
    -   Le *tampon de la ligne d’implémentation,* qui contient la ligne de la base de données. (Ces tampons contiennent conceptuellement des données telles qu’elles sont écrites ou lues à partir de la base de données. Toutefois, la forme stockée de données de base de données n’est pas spécifiée. Une base de données pourrait effectuer une conversion supplémentaire sur les données à partir de sa forme dans le tampon de mise en œuvre.)  
  
    -   Le *tampon de la ligne d’application,* qui contient la ligne de données présentée à l’application, suite à toute conversion de données que l’application peut spécifier.  
  
     L’application fonctionne sur le descripteur de la ligne d’application dans tous les cas où les données de colonne de la base de données doivent apparaître dans les variables d’application. Pour réaliser la conversion des données de colonne, l’application peut spécifier différents types de données de ceux du descripteur de la ligne d’implémentation.  
  
 Les types descripteur sont résumés dans le tableau suivant.  
  
|Type tampon|Lignes|Paramètres dynamiques|  
|-----------------|----------|------------------------|  
|**Mémoire tampon d’application**|Descripteur de ligne d’application (ARD)|Descripteur de paramètre d’application (APD)|  
|**Tampon de mise en œuvre**|Descripteur de ligne de mise en œuvre (IRD)|Descripteur de paramètre de mise en œuvre (IPD)|  
  
 Pour le paramètre ou les tampons de ligne, si l’application spécifie différents types de données dans les enregistrements correspondants des descripteurs de mise en œuvre et d’application, le pilote effectue la conversion des données lorsqu’il utilise les descripteurs. Par exemple, il peut convertir les valeurs numériques et datetimes en format caractère-corde. (Pour les conversions valides, voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).)  
  
 Un descripteur peut jouer différents rôles. Différentes déclarations peuvent partager n’importe quel descripteur que l’application attribue explicitement. Un descripteur de ligne dans une déclaration peut servir de descripteur de paramètre dans une autre déclaration.  
  
 On sait toujours si un descripteur donné est un descripteur d’application ou un descripteur de mise en œuvre, même si le descripteur n’a pas encore été utilisé dans une opération de base de données. Pour les descripteurs que la mise en œuvre attribue implicitement, la mise en œuvre enregistre la rangée prédéfinie par rapport à la poignée de déclaration. Tout descripteur que l’application attribue en appelant **SQLAllocHandle** est un descripteur d’application.
