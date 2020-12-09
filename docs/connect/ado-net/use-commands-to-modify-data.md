---
title: Utilisation des Commandes pour modifier les données
description: Explique comment utiliser un fournisseur de données pour exécuter des procédures stockées ou des instructions DDL (Data Definition Language).
ms.date: 11/25/2020
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 03ebdbdd15adfae8e765964e8338f043999319f3
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428199"
---
# <a name="using-commands-to-modify-data"></a>Utilisation des commandes pour modifier les données

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

À l’aide du Fournisseur de données Microsoft SqlClient pour SQL Server, vous pouvez exécuter des procédures stockées ou des instructions de langage de définition de données (par exemple, CREATE TABLE et ALTER COLUMN) pour effectuer une manipulation de schéma sur une base de données ou un catalogue. Ces commandes ne retournent pas des lignes comme une requête le ferait, donc l'objet <xref:Microsoft.Data.SqlClient.SqlCommand> fournit une méthode <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> pour les traiter.

Vous pouvez utiliser la méthode **ExecuteNonQuery** pour modifier le schéma mais utiliser cette méthode pour traiter les instructions SQL qui modifient les données mais ne retournent pas de lignes telles que INSERT, UPDATE et DELETE.

Bien que la méthode **ExecuteNonQuery** ne retourne pas de lignes, les paramètres d’entrée et de sortie et les valeurs de retour peuvent être passés et retournés via la collection **Parameters** de l’objet **Commande**.

## <a name="in-this-section"></a>Dans cette section

[La mise à jour des données dans une source de données](update-data-inside-data-source.md) explique comment exécuter des commandes ou des procédures stockées qui modifient les données d’une base de données.

[Exécution d’opérations de catalogue](perform-catalog-operations.md) décrit comment exécuter des commandes qui modifient le schéma de base de données.

## <a name="see-also"></a>Voir aussi

- [Récupération et modification de données dans ADO.NET](retrieving-modifying-data.md)
- [Commandes et paramètres](commands-parameters.md)
