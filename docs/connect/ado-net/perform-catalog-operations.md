---
title: Exécution d'opérations du catalogue
description: Décrit l'exécution des commandes qui modifient le schéma de base de données.
ms.date: 11/25/2020
dev_langs:
- csharp
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 85e68bd77b11fd70e4071d7ae67ebf26c643b540
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428203"
---
# <a name="performing-catalog-operations"></a>Exécution d'opérations du catalogue

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Pour exécuter une commande permettant de modifier une base de données ou un catalogue, comme l'instruction CREATE TABLE ou CREATE PROCEDURE, créez un objet **Commande** à l'aide des instructions SQL appropriées et d'un objet **Connexion**. Exécutez la commande avec la méthode <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> de l’objet <xref:Microsoft.Data.SqlClient.SqlCommand>.

## <a name="example"></a>Exemple

L'exemple de code suivant crée une procédure stockée dans une base de données Microsoft SQL Server.

[!code-csharp[DataWorks SqlCommand.ExecuteNonQuery#3](~/../sqlclient/doc/samples/SqlCommand_ExecuteNonQuery_SP_DML.cs#3)]

## <a name="see-also"></a>Voir aussi

- [Utilisation des commandes pour modifier les données](use-commands-to-modify-data.md)
- [Commandes et paramètres](commands-parameters.md)
