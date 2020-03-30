---
title: Guide pratique pour afficher les propriétés d’une instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bce9b82-7bbd-41df-b3f4-4b40b8bad474
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eaf4308f05b7a7fb1f450947754736d0cf565b61
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71294672"
---
# <a name="how-to-view-the-cdc-instance-properties"></a>Procédure : afficher les propriétés d'une instance de capture de données modifiées

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Cette procédure décrit comment utiliser la console du concepteur CDC pour afficher des informations sur les instances que vous créez afin d'aider à gérer le fonctionnement des instances.  
  
### <a name="to-view-information-about-a-specific-instance"></a>Pour afficher des informations sur une instance spécifique  
  
1.  Dans le menu **Démarrer** , sélectionnez **Console du concepteur de capture de données modifiées**.  
  
2.  Dans le volet gauche, développez **Capture de données modifiées** , puis le service qui contient l'instance que vous souhaitez afficher.  
  
3.  Sélectionnez le nom de l'instance à utiliser.  
  
     Les informations sur l'instance s'affichent dans la partie centrale de la console du concepteur de capture de données modifiées. Elles sont réparties en quatre onglets. Tous les onglets sont en lecture seule.  
  
     **État**  
     Cet onglet présente des informations sur l'état actuel de la capture de données modifiées pour l'instance. Pour plus d'informations sur ce qui est affiché dans cet onglet, consultez la section **Onglets de la visionneuse** dans [Manage a CDC Instance](../../integration-services/change-data-capture/manage-a-cdc-instance.md).  
  
     **Oracle**  
     Cet onglet affiche des informations générales sur l'instance de capture de données modifiées et la base de données source Oracle. Pour plus d'informations sur ce qui est affiché dans cet onglet, consultez [Edit the Oracle Database Properties](../../integration-services/change-data-capture/edit-the-oracle-database-properties.md).  
  
     **Tables**  
     Cet onglet affiche des informations sur les tables incluses dans la capture de données modifiées. Il répertorie également les colonnes qui sont capturées. Pour plus d'informations sur ce qui est affiché dans cet onglet, consultez [Edit Tables](../../integration-services/change-data-capture/edit-tables.md).  
  
     **Avancée**  
     Cet onglet contient une liste de propriétés avancées que vous définissez dans l'éditeur de propriétés. Pour plus d'informations sur ce qui est affiché dans cet onglet, consultez [Edit the Advanced Properties](../../integration-services/change-data-capture/edit-the-advanced-properties.md).  
  
  
