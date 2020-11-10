---
title: Azure Arc enabled SQL Server- Notes de publication
description: Dernières notes de publication
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 10/29/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3dcbc6b17d5abe87aabe923d70746d65595b9de6
ms.sourcegitcommit: dc3ea1696b8a4332934568439aed6cce4e9737eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93244651"
---
# <a name="release-notes---azure-arc-enabled-sql-server-preview"></a>Notes de publication - Azure Arc enabled SQL Server (préversion)

> [!NOTE]
> En tant que fonctionnalité en préversion, la technologie présentée dans cet article est soumise aux [conditions d’utilisation supplémentaires des préversions de Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

## <a name="september-2020"></a>Septembre 2020

Azure Arc enabled SQL Server est disponible en préversion publique. Il étend les services Azure aux instances SQL Server hébergées en dehors d’Azure dans le centre de données du client, à la périphérie ou dans un environnement multicloud.

Pour plus d’informations, consultez [Vue d’ensemble d’Azure Arc enabled SQL Server](overview.md)

### <a name="known-issues"></a>Problèmes connus

Les problèmes suivants concernent la version de septembre :

* Le panneau **Inscrire Azure Arc enabled SQL Server** ne prend pas en charge la configuration d’étiquettes personnalisées. Pour ajouter des étiquettes personnalisées, ouvrez la ressource **SQL Server - Azure Arc** après l’inscription et modifiez les étiquettes dans la page **Vue d’ensemble**.

* Pour connecter des instances SQL Server à Azure Arc, un compte avec un grand nombre d’autorisations est nécessaire. Pour plus d’informations, consultez [Autorisations requises](overview.md#required-permissions).

## <a name="october-2020"></a>Octobre 2020

La mise à jour d’octobre inclut les améliorations suivantes :

* Le panneau Inscrire Azure Arc enabled SQL Server comprend désormais l’onglet **Étiquettes**. Les étiquettes sont incluses dans le script d’inscription et sont reflétées dans les ressources **SQL Server - Azure Arc**. Pour plus d’informations, consultez [Connecter votre SQL Server à Azure Arc](connect.md).

* L’entrée **Intégrité de l’environnement** prend désormais en charge l’activation de **SQL Assessment** à partir du portail par le biais du déploiement d’un *CustomScriptExtension*. Pour plus d’informations, consultez [Configurer SQL Assessment](assess.md#run-on-demand-sql-assessment).

### <a name="known-issues"></a>Problèmes connus

Les problèmes suivants concernent la version d’octobre :

* Pour connecter des instances SQL Server à Azure Arc, un compte avec un grand nombre d’autorisations est nécessaire. Pour plus d’informations, consultez [Autorisations requises](overview.md#required-permissions).

## <a name="next-steps"></a>Étapes suivantes

**Vous voulez juste essayer ?**  Devenez vite opérationnel avec le [guide de démarrage rapide d’Azure Arc enabled SQL Server](https://aka.ms/AzureArcSqlServerJumpstart).
