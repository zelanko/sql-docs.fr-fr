---
title: Accès à l’intégration des Services Service | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6fdae3756442b1af660095fe53cbc8e4e3db82da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041421"
---
# <a name="access-to-the-integration-services-service"></a>Accéder au service Integration Services
  Les niveaux de protection des packages peuvent définir des restrictions quant aux utilisateurs autorisés à modifier et exécuter un package. Une protection supplémentaire est nécessaire pour limiter les utilisateurs autorisés à afficher la liste des packages actuellement en cours d’exécution sur un serveur et ceux qui peuvent arrêter les packages en cours d’exécution dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] utilise le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour établir la liste des packages en cours d'exécution. Les membres du groupe Administrateurs de Windows peuvent afficher et arrêter tous les packages en cours d'exécution. Les utilisateurs n'appartenant pas au groupe Administrateurs de Windows ne peuvent afficher et arrêter que les packages qu'ils ont démarrés.  
  
 Il est important de restreindre l'accès aux ordinateurs qui exécutent un service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , notamment un service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui peut énumérer des dossiers distants. Tout utilisateur authentifié peut demander l'énumération des packages. Même si le service ne trouve pas le service, il énumère les dossiers. Ces noms de dossiers peuvent être utilisés par un utilisateur malveillant. Si un administrateur a configuré le service pour qu'il énumère les dossiers sur un ordinateur distant, les utilisateurs peuvent également voir des noms de dossiers qu'ils ne pourraient pas voir en temps normal.  
  
  