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
ms.openlocfilehash: 41b139d2f22a9cb3137879d96224b02eafc24bab
ms.sourcegitcommit: c127c0752e84cccd38a7e23ac74c0362a40f952e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761497"
---
# <a name="connection-pooling"></a>Regroupement de connexions

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Se connecter à une source de données peut prendre beaucoup de temps. Pour minimiser le coût de l'ouverture de connexions, ADO.NET utilise une technique d'optimisation nommée *mise en pool de connexions*, qui limite le coût des ouvertures et fermetures des connexions à répétition.

## <a name="in-this-section"></a>Dans cette section  

[Regroupement de connexions SQL Server (ADO.NET)](sql-server-connection-pooling.md)  
Fournit une vue d’ensemble du regroupement de connexions et décrit son fonctionnement dans SQL Server.

## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-modifying-data.md)
- [Microsoft ADO.NET pour SQL Server](microsoft-ado-net-sql-server.md)
