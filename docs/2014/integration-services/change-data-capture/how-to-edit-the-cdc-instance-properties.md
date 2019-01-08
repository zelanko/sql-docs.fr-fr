---
title: Guide pratique pour modifier les propriétés d’une instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7a6c719a-3735-43b7-b3ab-dfadd325eca2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b2d15f17b867cd02d700ce6c749edddaa2c65083
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772941"
---
# <a name="how-to-edit-the-cdc-instance-properties"></a>Procédure : modifier les propriétés d'une instance de capture de données modifiées
  Cette procédure décrit comment utiliser la console du concepteur CDC pour modifier les propriétés de configuration d'une instance de capture de données modifiées.  
  
### <a name="to-edit-the-cdc-instance-configuration-properties"></a>Pour modifier les propriétés de configuration de l'instance de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Console du concepteur de capture de données modifiées**.  
  
2.  Dans le volet gauche, développez **Capture de données modifiées** , puis le service qui contient l'instance avec les propriétés à modifier.  
  
3.  Sélectionnez le nom de l'instance où vous souhaitez modifier les propriétés.  
  
4.  Dans le volet Actions à droite de la console du concepteur CDC, cliquez sur **Propriétés**.  
  
     Vous pouvez aussi cliquer avec le bouton droit sur l’instance dont vous voulez modifier les propriétés et cliquer sur **Propriétés**.  
  
5.  Dans l'éditeur de propriétés, modifiez les propriétés dans les onglets suivants :  
  
    -   **Oracle**: Utilisez le **Oracle** onglet dans l’éditeur de propriétés pour apporter des modifications à la description que vous avez fourni dans la page de base de données CDC créer dans l’Assistant Nouvelle Instance et pour apporter des modifications aux informations de connexion de base de données Oracle journal d’exploration de données.  
  
         Pour plus d'informations sur ce que vous pouvez modifier dans cet onglet, consultez [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).  
  
    -   **Tables**: Utilisez l'onglet **Tables** pour apporter des modifications aux tables et aux colonnes sélectionnées dans la base de données source Oracle.  
  
         Pour plus d'informations sur ce que vous pouvez modifier dans cet onglet, consultez [Edit Tables](edit-tables.md).  
  
    -   **Scripts**: Utilisez le **Scripts** onglet à exécuter ou réexécuter un script sur la base de données source Oracle qui configure une journalisation supplémentaire.  
  
         Pour plus d'informations sur ce que vous pouvez faire dans cet onglet, consultez [Review and Generate Supplemental Logging Scripts](review-and-generate-supplemental-logging-scripts.md).  
  
    -   **Avancé** : Utilisez l'onglet **Avancé** pour ajouter des propriétés spéciales à l'instance de capture de données modifiées.  
  
         Pour plus d'informations sur ce que vous pouvez faire dans cet onglet, consultez [Edit the Advanced Properties](edit-the-advanced-properties.md).  
  
  
