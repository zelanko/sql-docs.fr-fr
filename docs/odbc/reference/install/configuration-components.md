---
description: Composants de configuration
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a8a4b0f0b0a7a99409b5bb9caea53f23b62457e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487432"
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
