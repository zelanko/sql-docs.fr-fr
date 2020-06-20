---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b63be325273e4df33d837ec1548ed46701323977
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967869"
---
# <a name="mssqlserver_17130"></a>MSSQLSERVER_17130
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
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
  
  
