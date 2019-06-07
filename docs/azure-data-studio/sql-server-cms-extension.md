---
title: Extension de serveurs de gestion centralisée de SQL Server
titleSuffix: Azure Data Studio
description: Installer et utiliser l’extension de serveurs de gestion centralisée de SQL Server (version préliminaire) pour Azure Data Studio
ms.custom: seodec18
ms.date: 06/06/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 1d10e3c4e9c1e1b2a6ce316902d4f70bbfac3740
ms.sourcegitcommit: 32dce314bb66c03043a93ccf6e972af455349377
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66748472"
---
# <a name="sql-server-central-management-servers-extension-preview"></a>Extension de serveurs de gestion centralisée de SQL Server (version préliminaire)
L’extension de serveurs de gestion centralisée permet aux utilisateurs de stocker une liste d’instances de SQL Server qui est organisée en un ou plusieurs groupes. Actions qui sont effectuées à l’aide d’un groupe CMS agissent sur tous les serveurs dans le groupe de serveurs.

Cette expérience est actuellement dans sa version préliminaire. Signaler des problèmes et demandes de fonctionnalités [ici](https://github.com/microsoft/azuredatastudio/issues).

![Extension CMS](media/sql-server-cms-extension/cms-list.png)

## <a name="install-the-sql-server-central-management-servers-extension"></a>Installer l’extension de serveurs de gestion centralisée de SQL Server

1. Pour ouvrir le Gestionnaire d’extensions et accéder aux extensions disponibles, sélectionnez l’icône des extensions ou **Extensions** dans le **vue** menu.
2. Sélectionner une extension disponible pour afficher ses détails.
1. Sélectionnez l’extension (serveurs SQL Server Central Administration) et **installer** il.

### <a name="how-do-i-start-central-management-servers"></a>Comment démarrer les serveurs de gestion centralisée ?
 Serveurs de gestion centralisée peuvent être affichés en cliquant sur l’icône de connexions (Ctrl/Cmd + G). La première fois que vous téléchargez l’extension, la vue CMS sera réduite, et vous pouvez l’ouvrir en cliquant sur **des serveurs d’administration centrale**

## <a name="next-steps"></a>Étapes suivantes
Pour en savoir plus sur le plan conceptuel sur les serveurs de gestion centralisée, [vous pouvez en savoir plus ici.](https://docs.microsoft.com/sql/ssms/register-servers/create-a-central-management-server-and-server-group)


