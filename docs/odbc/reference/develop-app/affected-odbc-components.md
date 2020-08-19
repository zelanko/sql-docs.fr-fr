---
description: Composants ODBC affectés
title: Composants ODBC affectés | Microsoft Docs
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
ms.openlocfilehash: 4874a22d441ec856c25e08dc20cf04e0f0be89cd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424861"
---
# <a name="affected-odbc-components"></a>Composants ODBC affectés
Compatibilité descendante décrit la façon dont les applications, le gestionnaire de pilotes et les pilotes sont affectés par l’introduction d’une nouvelle version du gestionnaire de pilotes. Cela affecte les applications et le pilote lorsque l’un ou l’autre, ou les deux, sont conservés dans l’ancienne version. Il existe, par conséquent, trois types de compatibilité descendante à prendre en compte, comme indiqué dans le tableau suivant.  
  
|Type|Version de DM|Version de l’application|Version du pilote|  
|----------|-------------------|----------------------------|-----------------------|  
|Compatibilité descendante du gestionnaire de pilotes|*3.x*|*2.x*|*2.x*|  
|Compatibilité descendante du pilote [1]|*3.x*|*2.x*|*3.x*|  
|Compatibilité descendante de l’application|*3.x*|*3.x*|*2.x*|  
  
 [1] la compatibilité descendante des pilotes est principalement décrite dans annexe G : instructions relatives aux pilotes pour la compatibilité descendante.  
  
> [!NOTE]
>  Une application conforme aux normes, par exemple, une application qui a été écrite conformément aux normes Open Group ou ISO CLI, est garantie de fonctionner avec un pilote ODBC *3. x* par le biais du gestionnaire de pilotes ODBC *3. x* . Il est supposé que la fonctionnalité utilisée par l’application est disponible dans le pilote. Il est également supposé que l’application conforme aux normes a été compilée avec les fichiers d’en-tête ODBC *3. x* .
