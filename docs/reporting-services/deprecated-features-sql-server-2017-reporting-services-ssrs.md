---
title: Fonctionnalités déconseillées de SQL Server 2017 Reporting Services | Microsoft Docs
description: Cet article décrit les fonctionnalités qui seront déconseillées dans la prochaine version de SQL Server Reporting Services.
ms.date: 11/20/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d8fe51ce9d86688669e84ad866ad9f5e6da075e8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "74320313"
---
# <a name="deprecated-features-in-sql-server-2017-reporting-services"></a>Fonctionnalités déconseillées dans SQL Server 2017 Reporting Services

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017](../includes/ssrs-appliesto-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

Lorsqu’une fonctionnalité est marquée comme déconseillée, cela signifie que :

- La fonctionnalité est en mode de maintenance uniquement. Aucune nouvelle modification ne sera apportée, notamment les modifications liées à l’interopérabilité avec de nouvelles fonctionnalités.
- Nous nous efforçons de ne pas retirer une fonctionnalité déconseillée des futures versions pour faciliter les mises à niveau. Cependant, dans de rares cas, nous pouvons décider de retirer définitivement une fonctionnalité de Reporting Services si elle limite de futures innovations.
- Pour un nouveau travail de développement, nous vous recommandons de ne pas utiliser des fonctionnalités déconseillées.

## <a name="features-deprecated-in-the-next-version-of-sql-server"></a>Fonctionnalités dépréciées dans la prochaine version de SQL Server

Les fonctionnalités de SQL Server 2017 Reporting Services suivantes seront déconseillées dans la prochaine version de SQL Server. Évitez d’utiliser ces fonctionnalités dans vos nouveaux développements et modifiez dès que possible les applications qui y ont recours.

> [!NOTE]
> Cette liste est identique à la liste SQL Server 2016 Reporting Services (13.x). Aucune nouvelle fonctionnalité déconseillée ou abandonnée n’a été annoncée pour SQL Server 2017 Reporting Services (14.x).


| **Catégorie** | **Fonctionnalité déconseillée** | **Remplacement** |
| --- | --- | --- |
| Serveur de rapports | Renderer HTML 4.0. | Renderer HTML 5 |

## <a name="see-also"></a>Voir aussi

[Fonctionnalité abandonnée in SQL Server Reporting Services (SSRS)](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
