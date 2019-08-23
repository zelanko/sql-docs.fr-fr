---
title: Connecteur Microsoft pour Oracle | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0ad547d26c86c43b0009cdf20acae33ed7e8ab7
ms.sourcegitcommit: 57e20b7d02853ec9af46b648106578aed133fb45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69553241"
---
# <a name="microsoft-connector-for-oracle"></a>Connecteur Microsoft pour Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Le connecteur Microsoft pour Oracle permet d’exporter et de charger des données dans une source de données Oracle dans un package SSIS.

## <a name="version-support"></a>Prise en charge de version

Les produits Microsoft SQL Server suivants sont pris en charge par le connecteur Microsoft pour Oracle :

- À compter de SQL Server 2019
- SQL Server Data Tools (SSDT)

Les versions de base de données Oracle suivantes sont prises en charge pour la source de données :

- Oracle 10.x
- Oracle 11.x
- Oracle 12c
- Oracle 18c (sans prise en charge de l’authentification Windows)

La base de données Oracle est prise en charge sur tous les systèmes d’exploitation et plateformes.
> [!NOTE]
>
> Le client Oracle n’est pas nécessaire pour le connecteur Microsoft pour Oracle Database dans SQL Server 2019.

## <a name="installation"></a>Installation

Si vous devez exécuter le package dans SQL Server, vous pouvez obtenir le programme d’installation du connecteur Microsoft pour Oracle Database à [cet emplacement](https://www.microsoft.com/en-us/download/details.aspx?id=58228). Suivez les instructions dans l'assistant d'installation.

Après avoir installé le connecteur, vous devez redémarrer le service d’intégration SQL Server pour vous assurer que la source et la destination Oracle fonctionnent correctement.

Si vous avez besoin de concevoir un package avec le connecteur, vous n’avez pas besoin de télécharger le connecteur. SQL Server Data Tools (SSDT) le contient depuis la version 15.9.0.

## <a name="uninstallation"></a>Désinstallation

Vous pouvez exécuter l’Assistant de désinstallation pour supprimer le connecteur Microsoft pour Oracle Database de SQL Server.

## <a name="design-ssis-package-with-previous-version"></a>Concevoir un package SSIS avec une version précédente

Depuis la version 15.9.0, SSDT comprend déjà le connecteur Microsoft pour Oracle Database ; vous n’avez pas besoin d’effectuer d’installation lors de la conception de packages SSIS ciblant SQL Server 2019.

Pour concevoir un package SSIS ciblant SQL Server 2017 et antérieur, vous devez installer le connecteur pour Oracle par Attunity avec la version correspondante.

**Liens de téléchargement :**

- [SQL Server 2017 : Connecteur Microsoft Version 5.0 pour Oracle par Attunity](https://www.microsoft.com/en-us/download/details.aspx?id=55179)
- [SQL Server 2016 : Connecteur Microsoft Version 4.0 pour Oracle par Attunity](https://www.microsoft.com/en-us/download/details.aspx?id=52950)
- [SQL Server 2014 : Connecteur Microsoft Version 3.0 pour Oracle par Attunity](https://www.microsoft.com/en-us/download/details.aspx?id=44582)
- [SQL Server 2012 : Connecteur Microsoft Version 2.0 pour Oracle par Attunity](https://www.microsoft.com/en-us/download/details.aspx?id=29283)

## <a name="next-steps"></a>Étapes suivantes

- Configurer le [Gestionnaire de connexions Oracle](oracle-connection-manager.md).
- Configurer la [Source Oracle](oracle-source.md).
- Configurer la [Destination Oracle](oracle-destination.md).
- Si vous avez des questions, rendez-vous sur [TechCommunity](https://aka.ms/AA5u35j).
