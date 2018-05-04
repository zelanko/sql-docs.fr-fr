---
title: Composants de configuration | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9f3796703c2e778f9685714dcae2f541aa2b9a8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-components"></a>Composants de configuration
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Sources de données sont configurés par le programme d’installation de la DLL, qui dans le pilote appelle activer le programme d’installation DLL et le programme d’installation de traducteur DLL comme ils sont nécessaires. Le programme d’installation DLL est soit appelée directement depuis le panneau de configuration ou chargé et appelé par un autre programme, appelé le *du programme d’administration*. L’illustration suivante montre la relation entre les composants de configuration.  
  
 ![Relation entre composants de configuration](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Pour plus d’informations sur ces composants, consultez les rubriques suivantes à la fin de cette section.  
  
-   [Programme d’installation](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL d’installation](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de configuration de pilote](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Composants d’installation](../../../odbc/reference/install/installation-components.md)
