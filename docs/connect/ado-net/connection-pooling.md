---
title: Regroupement de connexions
description: En savoir plus sur la mise en pool des connexions, une technique d’optimisation utilisée par ADO.NET pour réduire le coût de l’ouverture des connexions aux sources de données.
ms.date: 11/13/2020
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 41842a2eb754aedc31bad206ad427a86bb65f00f
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96126421"
---
# <a name="connection-pooling"></a>Regroupement de connexions

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Se connecter à une source de données peut prendre beaucoup de temps. Pour minimiser le coût de l'ouverture de connexions, ADO.NET utilise une technique d'optimisation nommée *mise en pool de connexions*, qui limite le coût des ouvertures et fermetures des connexions à répétition.

## <a name="in-this-section"></a>Dans cette section  

[Le regroupement de connexions SQL Server (ADO.NET)](sql-server-connection-pooling.md) fournit une vue d'ensemble du regroupement de connexions et décrit son fonctionnement dans SQL Server.

## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-modifying-data.md)
