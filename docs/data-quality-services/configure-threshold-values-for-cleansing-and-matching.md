---
title: Configurer les valeurs de seuil pour le nettoyage et la correspondance
description: Découvrez comment configurer les valeurs de seuil qui seront utilisées pendant les activités de nettoyage et de correspondance assistées par ordinateur dans SQL Server Data Quality Services (DQS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: swinarko
ms.author: sawinark
ms.openlocfilehash: a0bcf7bc1cdf28aae4fc281f14f8edeec9f6c47d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "76916310"
---
# <a name="configure-threshold-values-for-cleansing-and-matching---data-quality-services-dqs"></a>Configurer les valeurs de seuil pour le nettoyage et la correspondance-Data Quality Services (DQS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Cette rubrique explique comment configurer les valeurs de seuil qui seront utilisées pendant les activités de nettoyage et de correspondance assistées par ordinateur dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_administrator sur la base de données DQS_MAIN pour configurer ces valeurs de seuil.  
  
##  <a name="Configure"></a>Configuration des valeurs de seuil  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Configuration**.  
  
3.  Ensuite, cliquez sur l’onglet **paramètres généraux** . Cet onglet vous permet de spécifier des valeurs de seuil pour les activités de nettoyage et de correspondance.  
  
4.  Pour spécifier des valeurs de seuil pour l'activité de nettoyage, spécifiez les valeurs appropriées dans les zones suivantes sous la zone **Nettoyage interactif** :  
  
    -   **Score minimum pour les suggestions**: score minimal ou niveau de confiance qui sera utilisé par DQS pour suggérer des remplacements d’une valeur pendant le processus de nettoyage assisté par ordinateur. Entrez une valeur en notation décimale de la valeur de pourcentage correspondante. Par exemple, tapez 0,75 pou 75 %. Cette valeur doit être inférieure ou égale à la valeur spécifiée dans la zone **Score minimal pour les corrections automatiques** . La valeur par défaut est 0,7.  
  
    -   **Score minimal pour les corrections automatiques**: score minimal ou niveau de confiance qui sera utilisé par DQS pour corriger automatiquement une valeur pendant le processus de nettoyage assisté par ordinateur. Entrez une valeur en notation décimale de la valeur de pourcentage correspondante. Par exemple, entrez 0,9 pour 90 %. La valeur par défaut est 0,8.  
  
5.  Pour spécifier la valeur de seuil pour l'activité de correspondance, spécifiez une valeur dans la zone **Score d'enregistrement minimal** sous la zone **Correspondance** . Cette valeur représente le score minimal pour qu'un enregistrement soit considéré comme une correspondance d'un autre enregistrement. La valeur par défaut est 80 %.  
  
6.  Cliquez sur **Fermer**.  
  
  
