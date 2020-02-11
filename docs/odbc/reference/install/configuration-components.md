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
ms.openlocfilehash: 248a9e31b176444ad51cb3a62c7c5f12f1b7bde3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068586"
---
# <a name="configuration-components"></a>Composants de configuration
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 Les sources de données sont configurées par la DLL du programme d’installation, qui à son tour appelle les dll d’installation du pilote et les dll d’installation du convertisseur, selon les besoins. La DLL du programme d’installation est soit appelée directement à partir du panneau de configuration, soit chargée et appelée par un autre programme, appelé *programme d’administration*. L’illustration suivante montre la relation entre les composants de configuration.  
  
 ![Relation entre composants de configuration](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Pour plus d’informations sur ces composants, consultez les rubriques suivantes à la fin de cette section.  
  
-   [Programme d’installation](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL d’installation](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de configuration de pilote](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Composants d’installation](../../../odbc/reference/install/installation-components.md)
