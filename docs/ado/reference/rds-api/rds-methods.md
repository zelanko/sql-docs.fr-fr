---
description: Méthodes RDS
title: Méthodes RDS | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- RDS methods [ADO]
- methods [ADO], RDS
ms.assetid: c2c6af1a-3c44-4c9d-ad33-b381552c71af
author: rothja
ms.author: jroth
ms.openlocfilehash: 7f8685ead3b7f62861d6e27792a850af3140ebe3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438791"
---
# <a name="rds-methods"></a>Méthodes RDS
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Méthode|Description|  
|-|-|  
|[Annuler (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)|Annule l’exécution d’un appel de méthode asynchrone en attente.|  
|[CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)|Annule toutes les modifications apportées à la ligne actuelle ou nouvelle d’un objet **Recordset** .|  
|[ConvertToString (RDS)](../../../ado/reference/rds-api/converttostring-method-rds.md)|Convertit un **Recordset** en une chaîne MIME qui représente les données du Recordset.|  
|[CreateObject (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)|Crée le proxy pour l’objet métier cible et retourne un pointeur vers celui-ci.|  
|[CreateRecordset (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)|Crée un **jeu d’enregistrements**vide et déconnecté.|  
|[Execute, méthode (RDS)](../../../ado/reference/rds-api/execute-method-rds.md)|Exécutez la demande et créez un ensemble de lignes de données avancé (pour une utilisation avec ADO 2,5 et versions ultérieures).|  
|[Execute21, méthode (RDS)](../../../ado/reference/rds-api/execute21-method-rds.md)|Exécutez la demande et créez un ensemble de lignes de données avancé (pour une utilisation avec ADO 2,1).|  
|[InvokeService (RDS)](../../../ado/reference/rds-api/invokeservice-rds.md)|Retourne un pointeur vers l’interface demandée sur une version plus puissante de l’objet.|  
|[MoveFirst, MoveLast, MoveNext, MovePrevious (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)|Passe au premier enregistrement, dernier, suivant ou précédent dans un objet **Recordset** spécifié.|  
|[Requête (RDS)](../../../ado/reference/rds-api/query-method-rds.md)|Utilise une chaîne de requête SQL valide pour retourner un **jeu d’enregistrements**.|  
|[Actualiser (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)|Interroge à jour la source de données spécifiée dans la propriété **Connect** et met à jour les résultats de la requête.|  
|[Réinitialisation (RDS)](../../../ado/reference/rds-api/reset-method-rds.md)|Exécute le tri ou le filtre sur un **jeu d’enregistrements**côté client, en fonction des propriétés de tri et de filtre spécifiées.|  
|[SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)|Soumet les modifications en attente de l' **objet Recordset** mis à jour et mis en cache localement à la source de données spécifiée dans la propriété **Connect** .|  
|[Synchronize, méthode (RDS)](../../../ado/reference/rds-api/synchronize-method-rds.md)|Synchronise le Recordset donné avec la base de données spécifiée par la chaîne de connexion (pour une utilisation avec ADO 2,5 et versions ultérieures).|  
|[Synchronize21, méthode (RDS)](../../../ado/reference/rds-api/synchronize21-method-rds.md)|Synchronise le Recordset donné avec la base de données spécifiée par la chaîne de connexion (pour une utilisation avec ADO 2,1).|


