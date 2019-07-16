---
title: Les Collections et les objets ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and collections
ms.assetid: 7a745aae-9372-49b6-8dae-b9c93e5f3216
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89093367532177ec87fb3a5fd86e38e98345962c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926041"
---
# <a name="ado-objects-and-collections"></a>Objets et collections ADO
ADO se compose de neuf objets suivants et quatre collections.  
  
|Objet ou une Collection|Description|  
|--------------------------|-----------------|  
|**Connexion** objet|Représente une session unique avec une source de données. Dans le cas d’un système de base de données client/serveur, il peut être équivalente à une connexion de réseau réelle au serveur. Selon les fonctionnalités prises en charge par le fournisseur, certaines collections, les méthodes ou les propriétés d’un **connexion** objet n’est peut-être pas disponible.|  
|Objet**Command**|Utilisé pour définir une commande spécifique, comme une requête SQL, conçue pour s’exécuter sur une source de données.|  
|**Jeu d’enregistrements** objet|Représente l’ensemble des enregistrements à partir d’une table de base ou les résultats d’une commande exécutée. Tous les **Recordset** objets sont constitués d’enregistrements (lignes) et des champs (colonnes).|  
|**Enregistrement** objet|Représente une ligne unique de données, à partir d’un **Recordset** ou à partir du fournisseur. Cet enregistrement peut représenter un enregistrement de base de données ou un autre type d’objet tel qu’un fichier ou répertoire, en fonction de votre fournisseur.|  
|**Stream** objet|Représente un flux de données binaire ou texte. Par exemple, un document XML peut être chargé dans un flux pour la commande entrée ou retournée à partir de certains fournisseurs que les résultats d’une requête. Un **Stream** objet peut être utilisé pour manipuler des champs ou enregistrements contenant ces flux de données.|  
|**Paramètre** objet|Représente un paramètre ou un argument associé à un **commande** objet basé sur une procédure stockée ou une requête paramétrable.|  
|**Champ** objet|Représente une colonne de données avec un type de données commun. Chaque **champ** objet correspond à une colonne dans la **Recordset**.|  
|**Propriété** objet|Représente une caractéristique d’un objet ADO qui est définie par le fournisseur. Objets ADO possèdent deux types de propriétés : intégrées et dynamiques. Les propriétés intégrées sont les propriétés implémentées dans ADO et immédiatement disponibles pour tout nouvel objet. Le **propriété** objet est un conteneur pour les propriétés dynamiques, définies par le fournisseur sous-jacent.|  
|Objet**Error**|Contient des détails sur les erreurs d’accès aux données qui se rapportent à une seule opération impliquant le fournisseur.|  
|**Champs** collection|Contient tous les **champ** objets d’un **Recordset** ou **enregistrement** objet.|  
|**Propriétés** collection|Contient tous les **propriété** objets pour une instance spécifique d’un objet.|  
|**Paramètres** collection|Contient tous les **paramètre** objets d’un **commande** objet.|  
|**Erreurs** collection|Contient tous les **erreur** objets créés en réponse à une erreur liée au fournisseur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md)
