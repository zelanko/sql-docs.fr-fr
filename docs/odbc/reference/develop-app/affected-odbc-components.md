---
title: Composants ODBC touchés (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d9155fa1c9df5846f069e93a3db1b969e9219ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306473"
---
# <a name="affected-odbc-components"></a>Composants ODBC affectés
La compatibilité rétrograde décrit comment les applications, le Driver Manager et les pilotes sont affectés par l’introduction d’une nouvelle version du Driver Manager. Cela affecte les applications et le pilote lorsque l’un ou l’autre d’entre eux restent dans l’ancienne version. Il existe donc trois types de compatibilité vers l’arrière à considérer, comme le montre le tableau suivant.  
  
|Type|Version de DM|Version de l’application|Version du pilote|  
|----------|-------------------|----------------------------|-----------------------|  
|Compatibilité rétrograde du Driver Manager|*3.x*|*2.x*|*2.x*|  
|Compatibilité rétrograde du conducteur[1]|*3.x*|*2.x*|*3.x*|  
|Compatibilité rétrograde de l’application|*3.x*|*3.x*|*2.x*|  
  
 [1] La compatibilité rétrograde des conducteurs est principalement discutée à l’Annexe G: Lignes directrices du conducteur pour la compatibilité vers l’arrière.  
  
> [!NOTE]
>  Une application conforme aux normes - par exemple, une application qui a été écrite conformément aux normes Open Group ou ISO CLI - est garantie de travailler avec un pilote ODBC *3.x* par l’intermédiaire de l’ODBC *3.x* Driver Manager. On suppose que la fonctionnalité que l’application utilise est disponible dans le pilote. On suppose également que l’application conforme aux normes a été compilée avec les fichiers d’en-tête ODBC *3.x.*
