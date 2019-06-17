---
title: Les composants ODBC affectés | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72e004e6fd41ee74643fc05ec9020e6ac1933e09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63186251"
---
# <a name="affected-odbc-components"></a>Composants ODBC affectés
Compatibilité descendante décrit comment les applications, le Gestionnaire de pilotes et les pilotes sont affectés par l’introduction d’une nouvelle version du Gestionnaire de pilotes. Cela affecte les applications et le pilote lorsqu’ou pour les deux d'entre eux restent dans l’ancienne version. Il existe, par conséquent, trois types de compatibilité descendante à prendre en compte, comme indiqué dans le tableau suivant.  
  
|type|Version de DM|Version de l’application|Version du pilote|  
|----------|-------------------|----------------------------|-----------------------|  
|Compatibilité descendante du Gestionnaire de pilotes|3 *.x*|2.*x*|2.*x*|  
|Compatibilité descendante de pilote [1]|3 *.x*|2.*x*|3.*x*|  
|Compatibilité descendante des applications|3.*x*|3.*x*|2.*x*|  
  
 [1] la compatibilité descendante des pilotes est principalement abordée dans g : annexe Instructions de pilote pour la compatibilité descendante.  
  
> [!NOTE]
>  Une application conforme aux normes - par exemple, une application qui a été écrit conformément aux normes Open Group ou ISO CLI - est garantie pour travailler avec un ODBC 3 *.x* pilote via l’ODBC 3 *.x*Gestionnaire de pilotes. Il est supposé que la fonctionnalité à l’aide de l’application est disponible dans le pilote. Il est également supposé que l’application conforme aux normes a été compilée avec l’ODBC 3 *.x* fichiers d’en-tête.
