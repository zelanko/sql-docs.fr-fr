---
author: MikeRayMSFT
ms.prod: sql
ms.technology: big-data-cluster
ms.topic: include
ms.date: 06/22/2020
ms.author: mikeray
ms.openlocfilehash: b72f8044638adbf75049392fae32447a8a749a6d
ms.sourcegitcommit: d973b520f387b568edf1d637ae37d117e1d4ce32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85215082"
---
À partir de SQL Server 2019 CU5, lorsque vous déployez un nouveau cluster avec l’authentification de base, tous les points de terminaison, dont la passerelle, utilisent `AZDATA_USERNAME` et `AZDATA_PASSWORD`. Les points de terminaison sur les clusters mis à niveau vers la CU5 continuent à utiliser `root` comme nom d’utilisateur pour se connecter au point de terminaison de la passerelle. Cette modification ne s’applique pas aux déploiements utilisant l’authentification Active Directory. Voir [Informations d’identification pour l’accès aux services via le point de terminaison de passerelle](../big-data-cluster/release-notes-big-data-cluster.md#credentials-for-accessing-services-through-gateway-endpoint) dans les notes de publication.