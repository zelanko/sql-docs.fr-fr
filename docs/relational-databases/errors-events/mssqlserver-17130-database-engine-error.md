---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 19fdbd6e3c8870e57acb81b4d1b923516da2b5a7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780864"
---
# <a name="mssqlserver_17130"></a>MSSQLSERVER_17130
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|17130|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NOLOCKSPACE|  
|Texte du message|Mémoire insuffisante pour le nombre de verrous configuré. Tentative de démarrage avec une table de hachage de verrou moins importante en cours, ce qui risque d'influer sur les performances. Contactez l'administrateur de base de données pour configurer une quantité de mémoire plus importante pour cette instance du moteur de base de données.|  
  
## <a name="explanation"></a>Explication  
Mémoire insuffisante pour la taille souhaitée de la table de hachage du gestionnaire de verrous.  Une tentative d'allocation d'une table de hachage plus petite va être effectuée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez les paramètres de configuration de la mémoire du serveur (min server memory et max server memory), ainsi que la sollicitation de la mémoire : Allouez davantage de mémoire à SQL Server.  
  
