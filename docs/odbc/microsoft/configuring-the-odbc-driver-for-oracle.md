---
description: Configuration du pilote ODBC pour Oracle
title: Configuration du pilote ODBC pour Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- configuring ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], configuring
ms.assetid: 0a5f827c-0b80-4627-85cb-f10292b9fb33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f53bf5efc66ad260c0184baf95a254313319da5d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483672"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Configuration du pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Vous pouvez contrôler les performances du pilote ODBC pour Oracle en connaissant l’environnement de données et en définissant correctement les paramètres de la connexion à la source de données via la boîte de dialogue [administrateur de sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md) ou à l’aide de paramètres de chaîne de connexion. La boîte de dialogue fournit les contrôles suivants pour la connexion à une source de données à l’aide de la boîte de dialogue ou à l’aide de chaînes de connexion :  
  
-   **Onglet DSN utilisateur** Répertorie les noms de sources de données qui sont locaux sur l’ordinateur.  
  
-   **Onglet DSN système** Vous permet d’ajouter ou de supprimer une source de données système. Les sources de données système sont accessibles par tous les utilisateurs sur l’ordinateur local.  
  
-   **Onglet DSN de fichier** Vous permet d’ajouter ou de supprimer une source de données de fichier de l’ordinateur local. Les sources de données de fichier peuvent être partagées par tous les utilisateurs qui ont le même pilote installé.  
  
-   **Onglet pilotes** Répertorie les pilotes ODBC installés.  
  
-   **Onglet suivi** Vous permet de spécifier la façon dont le gestionnaire de pilotes ODBC effectue le suivi des appels aux fonctions ODBC. Vous pouvez configurer le suivi séparément pour chaque application ODBC installée.  
  
-   **Onglet regroupement de connexions** Vous permet de sélectionner des options de connexion pour chaque pilote installé.  
  
-   **Onglet à propos de** Répertorie les fichiers de composants ODBC installés.  
  
 Après avoir ajouté une source de données, vous pouvez utiliser la boîte de dialogue administrateur de la **source de données ODBC** pour configurer l’accès à votre source de données. Sélectionnez une source de données, puis cliquez sur l’un des onglets pour modifier ou consulter les informations.
