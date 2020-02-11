---
title: Migrer des connexions SQL Server avec Assistant Migration de données
description: Découvrez comment migrer des connexions SQL Server avec Assistant Migration de données
ms.date: 10/22/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, login migration
ms.assetid: ''
author: HJToland3
ms.author: jtoland
ms.custom: seo-lt-2019
ms.openlocfilehash: 368372ab7324b11e9f7fdaa6af94d5ba2c0534ad
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056478"
---
# <a name="migrate-sql-server-logins-with-data-migration-assistant"></a>Migrer des connexions SQL Server avec Assistant Migration de données

Cet article fournit une vue d’ensemble de la migration des connexions SQL Server à l’aide de Assistant Migration de données.

> [!IMPORTANT]
> Cette rubrique s’applique aux scénarios qui impliquent des mises à niveau de SQL Server vers des versions ultérieures du produit local ou à des SQL Server sur des machines virtuelles Azure.

## <a name="which-logins-are-migrated"></a>Connexions à migrer

- Vous pouvez migrer les connexions basées sur un principal Windows (tel qu’un utilisateur de domaine ou un groupe de domaine Windows). Vous pouvez également migrer des connexions créées en fonction de l’authentification SQL, également appelées connexions SQL Server.

- Assistant Migration de données ne prend actuellement pas en charge les connexions associées à un certificat de sécurité autonome (connexions mappées au certificat), une clé asymétrique autonome (connexions mappées à une clé asymétrique) et des connexions mappées à des informations d’identification.

- Assistant Migration de données ne déplace pas la connexion **sa** et les principes du serveur avec les noms encadrés\#\#de doubles signes dièse (), qui sont destinés à un usage interne uniquement.

- Par défaut, Assistant Migration de données sélectionne toutes les connexions qualifiées à migrer. Si vous le souhaitez, vous pouvez sélectionner des connexions spécifiques à migrer. Lorsque Assistant Migration de données migre toutes les connexions qualifiées, le mappage de l’utilisateur de connexion reste intact dans les bases de données qui sont migrées.

  Si vous envisagez de migrer des connexions spécifiques, veillez à sélectionner les connexions qui sont mappées à un ou plusieurs utilisateurs dans les bases de données sélectionnées pour la migration.

- Dans le cadre de la migration de la connexion, Assistant Migration de données déplace également les rôles de serveur définis par l’utilisateur et ajoute des autorisations au niveau du serveur aux rôles de serveur définis par l’utilisateur. Le propriétaire du rôle est défini sur **sa** principal.

## <a name="during-and-after-migration"></a>Pendant et après la migration

- Dans le cadre de la migration de la connexion, Assistant Migration de données affecte les autorisations aux éléments sécurisables sur le SQL Server cible, tels qu’ils existent sur le SQL Server source.

  Si la connexion existe déjà sur le SQL Server cible, Assistant Migration de données migre uniquement les autorisations affectées aux éléments sécurisables et ne recrée pas la connexion entière.

- Assistant Migration de données permet de mapper la connexion aux utilisateurs de base de données si la connexion existe déjà sur le serveur cible.

- Il est recommandé de passer en revue les résultats de la migration pour comprendre l’état global de la migration de la connexion et toutes les actions de postconnexion recommandées.

## <a name="resources"></a>Ressources

[Assistant Migration de données (DMA)](../dma/dma-overview.md)

[Assistant Migration de données : paramètres de configuration](../dma/dma-configurationsettings.md)
