---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc163f53c9dc234702f6f74426eb65f57cec26b5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096685"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Configuration du pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Vous pouvez contrôler les performances du pilote ODBC pour Oracle par le fait de connaître l’environnement de données et définir correctement les paramètres de la connexion de source de données via le [administrateur de sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md) boîte de dialogue zone ou via connect paramètres de chaîne. La boîte de dialogue fournit les contrôles suivants pour la connexion à une source de données à l’aide de la boîte de dialogue ou à l’aide de chaînes de connexion :  
  
-   **Onglet DSN utilisateur** répertorie les noms de Source de données qui sont locales à l’ordinateur.  
  
-   **Onglet DSN système** vous permet d’ajouter ou supprimer une source de données système. Sources de données système sont accessibles par tous les utilisateurs sur l’ordinateur local.  
  
-   **Onglet de fichier DSN** vous permet d’ajouter ou supprimer une source de données de fichier à partir de l’ordinateur local. Fichiers sources de données peuvent être partagés par tous les utilisateurs qui ont le même pilote installé.  
  
-   **Onglet pilotes** répertorie les pilotes ODBC installés.  
  
-   **Onglet suivi** vous permet de spécifier comment le Gestionnaire de pilotes ODBC effectue le suivi des appels aux fonctions ODBC. Vous pouvez configurer le traçage séparément pour chaque application ODBC installée.  
  
-   **Onglet regroupement de connexions** vous permet de sélectionner des options de connexion pour chaque pilote installé.  
  
-   **Sur l’onglet** répertorie les fichiers de composant ODBC installés.  
  
 Après avoir ajouté une source de données, vous pouvez utiliser la **administrateur de sources de données ODBC** boîte de dialogue pour configurer l’accès à votre source de données. Sélectionnez une source de données, puis cliquez sur un des onglets pour modifier ou consulter les informations.
