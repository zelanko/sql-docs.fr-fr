---
title: Configurer le pilote ODBC pour Oracle (fr) Microsoft Docs
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
ms.openlocfilehash: 1bbdbe36ed9e6f254e2b738479698bd9eece09f8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281369"
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Configuration du pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Vous pouvez contrôler les performances du pilote ODBC pour Oracle en connaissant l’environnement de données et en définissant correctement les paramètres de la connexion source de données via la boîte de dialogue [ODBC Data Source Administrator](../../odbc/admin/odbc-data-source-administrator.md) ou via des paramètres de chaîne de connexion. La boîte de dialogue fournit les contrôles suivants pour se connecter à une source de données à l’aide de la boîte de dialogue ou à l’aide de chaînes de connexion :  
  
-   **Onglet DSN utilisateur** Répertorie les noms de source de données qui sont locaux à l’ordinateur.  
  
-   **Onglet DSN système** Vous permet d’ajouter ou de supprimer une source de données système. Toutes les sources de données système peuvent être consultées par tous les utilisateurs de l’ordinateur local.  
  
-   **Dossier DSN onglet** Vous permet d’ajouter ou de supprimer une source de données de fichiers à partir de l’ordinateur local. Les sources de données de fichiers peuvent être partagées par tous les utilisateurs qui ont installé le même pilote.  
  
-   **Onglet Pilotes** Répertorie les pilotes ODBC installés.  
  
-   **Onglet de traçage** Vous permet de spécifier comment le gestionnaire de pilote ODBC retrace les appels vers les fonctions D’ODBC. Vous pouvez configurer le traçage séparément pour chaque application ODBC installée.  
  
-   **Onglet de mise en commun de connexion** Vous permet de sélectionner les options de connexion pour chaque pilote installé.  
  
-   **À propos de l’onglet** Répertorie les fichiers de composants ODBC installés.  
  
 Après avoir ajouté une source de données, vous pouvez utiliser la boîte de dialogue **ODBC Data Source Administrator** pour configurer l’accès à votre source de données. Sélectionnez une source de données, puis cliquez sur l’un des onglets pour modifier ou examiner les informations.
