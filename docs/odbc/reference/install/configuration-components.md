---
title: Composants de configuration | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcf7d34f8faf70f57373ad1a5dae55261799145b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198408"
---
# <a name="configuration-components"></a>Composants de configuration
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Sources de données sont configurées par le programme d’installation DLL, qui, dans le pilote d’appels de désactiver le programme d’installation DLL et le programme d’installation de traducteur dll car ils sont nécessaires. Le programme d’installation DLL est soit appelée directement à partir du panneau ou chargé et appelé par un autre programme, appelé le *du programme d’administration*. L’illustration suivante montre la relation entre les composants de configuration.  
  
 ![Relation entre composants de configuration](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Pour plus d’informations sur ces composants, consultez les rubriques suivantes à la fin de cette section.  
  
-   [Programme d’installation](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL d’installation](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de configuration de pilote](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Composants d’installation](../../../odbc/reference/install/installation-components.md)
