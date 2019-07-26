---
ms.openlocfilehash: 2dc81d434714e0a13912fa6f14e1194df5e5afe3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215607"
---
> [!NOTE]
> Quand vous créez la ressource et régulièrement par la suite, l’agent de ressource Pacemaker définit automatiquement la valeur de `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` sur le groupe de disponibilité selon la configuration de celui-ci. Par exemple, si le groupe de disponibilité a trois réplicas synchrones, l’agent affecte à `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` la valeur `1`. Pour obtenir plus d’informations et d’options de configuration, consultez [Haute disponibilité et protection des données pour les configurations des groupes de disponibilité](../linux/sql-server-linux-availability-group-ha.md). 