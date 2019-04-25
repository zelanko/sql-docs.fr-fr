---
title: Paramètres (synchronisation) (MySQLToSQL) du projet | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 42061ff7-e6e7-497b-a0d9-440b9cf5986c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e82fa9d02fdbfe876f4097c54c6877c3a3a81fee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62473905"
---
# <a name="project-settings-synchronization-mysqltosql"></a>Paramètres du projet (Synchronisation) (MySQLToSQL)
La synchronisation **paramètres du projet** vous permettent de configurer la façon dont les objets de base de données MySQL sont synchronisés avec les objets de base de données SQL Server.  
  
Les actions par défaut spécifient les paramètres par défaut de l’actualisation des objets à partir de la base de données MySQL et pour la synchronisation des objets avec la base de données SQL Server. Pour plus d’informations, consultez [Actualiser à partir de la base de données &#40;MySQLToSQL&#41;](../../ssma/mysql/refresh-from-database-mysqltosql.md)  
  
Vous pouvez accéder à deux différentes pages de synchronisation qui contiennent les mêmes paramètres :  
  
-   Pour spécifier les paramètres pour tous les futurs projets SSMA, sur le **outils** menu, cliquez sur **DefaultProject paramètres**, puis cliquez sur **synchronisation** en bas du volet gauche.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, cliquez sur **paramètres du projet**, puis cliquez sur **synchronisation** en bas du volet gauche.  
  
## <a name="options"></a>Options  
  
##### <a name="misc"></a>Divers  
  
##### <a name="attempts"></a>Tentatives  
Fournit les informations sur le nombre de passages pour prennent des objets à charger dans SQL Server. Chargement des objets dans SQL Server est généralement effectué par plusieurs passes. Les objets qui ne parviennent pas à charger lors du premier passage, telles que les clés étrangères, peuvent se charger correctement dans la prochaine phase.  
  
Par défaut, la valeur est 2.  
  
## <a name="synchronization-for-mysql"></a>Synchronisation pour MySQL  
  
##### <a name="action-on-local-and-remote-object-change"></a>Action sur la modification de l’objet locaux et distants  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque la définition d’objet est modifié dans SSMA et sur le serveur de base de données.  
  
-   Si vous sélectionnez Actualiser à partir de la base de données, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez Ignorer, SSMA n’effectue aucune action d’actualisation.  
  
##### <a name="action-on-local-object-change"></a>Action sur la modification de l’objet local  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque l’objet est modifié dans SSMA.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
##### <a name="action-on-remote-object-change"></a>Action sur la modification de l’objet distant  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les objets sont modifiées sur le serveur de base de données.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Action lorsque les métadonnées de l’objet local sont manquantes  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les métadonnées locales sont manquante.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation  
  
## <a name="synchronization-for-sql-server"></a>Synchronisation pour SQL Server  
  
##### <a name="action-on-local-and-remote-object-change"></a>Action sur la modification de l’objet Local et distant  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque la définition d’objet est modifié dans SSMA et sur le serveur de base de données.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour les objets dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
##### <a name="action-on-local-object-change"></a>Action sur la modification de l’objet local  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque l’objet est modifié dans SSMA.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
##### <a name="action-on-remote-object-change"></a>Action sur la modification de l’objet distant  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les objets sont modifiées sur le serveur de base de données.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA chargera les définitions de base de données dans les métadonnées lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA met à jour l’objet dans la base de données en fonction du contenu des métadonnées SSMA lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>Action lorsque les métadonnées de l’objet local sont manquantes  
Spécifie le paramètre par défaut dans la boîte de dialogue de synchronisation lorsque les métadonnées locales sont manquante.  
  
-   Si vous sélectionnez **Actualiser à partir de la base de données**, SSMA sélectionne l’actualisation à partir de l’option de base de données lorsque la condition est remplie.  
  
-   Si vous sélectionnez **écrire dans la base de données**, SSMA supprimera l’objet à partir de la base de données lorsque la condition est remplie.  
  
-   Si vous sélectionnez **Skip**, SSMA n’effectuera pas les actions d’actualisation.  
  
