---
title: Migration des connexions SQL Server avec Data Migration Assistant | Microsoft Docs
description: Découvrez comment migrer des connexions SQL Server avec Data Migration Assistant
ms.custom: ''
ms.date: 03/12/2019
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
ms.author: rajpo
manager: jroth
ms.openlocfilehash: 25e60b4c51e6a4a5ac38a1b7f0e3268a0cee3e3b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794340"
---
# <a name="migrate-sql-server-logins-with-data-migration-assistant"></a>Migration des connexions SQL Server avec Data Migration Assistant

Cet article fournit une vue d’ensemble de la migration des connexions SQL Server à l’aide de Data Migration Assistant. 

## <a name="which-logins-are-migrated"></a>Les noms de connexion sont migrés.

- Vous pouvez migrer les connexions basées sur un principal Windows (par exemple, un utilisateur de domaine ou un groupe de domaine Windows). Vous pouvez également migrer les connexions créées en fonction de l’authentification SQL, appelée également les connexions SQL Server.

- Assistant Migration de données actuellement ne prend en charge les connexions associées à un certificat de sécurité autonomes (connexions mappés au certificat), une clé asymétrique autonome (connexions mappées à la clé asymétrique) et connexions mappées aux informations d’identification.

- Assistant Migration des données sans avoir à déplacer le **sa** principes de connexion et le serveur avec des noms délimitées par des doubles de hachage (\#\#), qui sont à usage interne uniquement.

- Par défaut, Data Migration Assistant sélectionne toutes les connexions qualifiées à migrer. Si vous le souhaitez, vous pouvez sélectionner des connexions spécifiques à migrer. Lorsque Data Migration Assistant migre toutes les connexions qualifiées, le mappage de connexion utilisateur reste intact dans les bases de données qui sont migrés. 

  Si vous projetez de migrer des connexions spécifiques, veillez à sélectionner les connexions qui sont mappées à un ou plusieurs utilisateurs dans les bases de données sélectionnées pour la migration.

- Dans le cadre de la migration de connexion, Data Migration Assistant également déplace les rôles serveur définis par l’utilisateur et ajoute les autorisations au niveau du serveur pour les rôles de serveur définis par l’utilisateur. Le propriétaire du rôle est défini sur **sa** principal.

## <a name="during-and-after-migration"></a>Pendant et après la migration

- Dans le cadre de la migration de connexion, Data Migration Assistant attribue les autorisations aux éléments sécurisables sur la cible de SQL Server tels qu’ils existent sur la source de SQL Server. 

  Si la connexion existe déjà sur la cible de SQL Server, Data Migration Assistant migre uniquement les autorisations affectées aux éléments sécurisables et ne sont pas recréer la connexion entière.

- Assistant Migration de données rend le meilleur effort pour mapper la connexion aux utilisateurs de base de données si la connexion existe déjà sur le serveur cible.

- Il est recommandé que vous passez en revue les résultats de la migration pour comprendre l’état général de la migration de connexion et les actions recommandées de post-migration.

## <a name="resources"></a>Ressources

[Data Migration Assistant (DMA)](../dma/dma-overview.md)

[Assistant de Migration de données : Paramètres de configuration](../dma/dma-configurationsettings.md)
