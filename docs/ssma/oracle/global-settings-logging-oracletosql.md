---
title: Paramètres globaux (journalisation) (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 12dbcd77-2b90-4fa1-9cf9-239231ea5773
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: abe73fd789a74d358c0573b6c0778a15612532a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710837"
---
# <a name="global-settings-logging-oracletosql"></a>Paramètres globaux (Journalisation) (OracleToSQL)
Utilisez le **paramètres globaux** boîte de dialogue pour spécifier les paramètres de journalisation pour SSMA. En règle générale, vous modifieriez ces paramètres uniquement lorsque vous travaillez avec le support technique.  
  
Pour accéder à cette boîte de dialogue, dans le **outils** menu, sélectionnez **paramètres globaux** puis cliquez sur le **journalisation** bouton en bas du volet gauche.  
  
## <a name="options"></a>Options  
**Niveau de messages**  
Les options suivantes sont disponibles sous **au niveau des Messages**:  
  
|Option|Description|  
|----------|---------------|  
|**[toutes les catégories]**|Utilisé pour définir le niveau de journalisation pour toutes les options suivantes.|  
|**Collecteur**|Collecte des métadonnées sur le schéma source et l’enregistre dans le projet.|  
|**Converter**|Convertit des objets de base de données source, tels que les tables et procédures stockées, des structures de correspondant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] structures.|  
|**Utilitaire de migration de données**|Migre les données à partir de la base de données source dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Formateur**|Sous-composant du convertisseur qui génère des scripts pour la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schéma.|  
|**Interface utilisateur graphique**|Messages qui s’affichent lorsque vous utilisez l’outil SSMA.|  
|**Éditeur de liens**|Résout les identificateurs SQL et fournit des informations à d’autres composants.|  
|**Autres**|Tous les messages qui ne sont pas dans une autre catégorie.|  
|**Analyseur**|Analyse du schéma source.|  
|**Synchronisateur**|Charge la source des objets de base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**TreeConverter**|Convertit des objets dans les métadonnées de source dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] métadonnées.|  
|**Testeur**|Messages qui s’affichent lorsque vous utilisez le testeur de SSMA.|  
  
Pour chaque option sous **au niveau des Messages**, configurez l’un des niveaux de journalisation suivants pour SSMA :  
  
|||  
|-|-|  
|**Erreur irrécupérable**|Écrire uniquement les messages d’erreur irrécupérable dans le journal.|  
|**Erreur**|Écrire des messages d’erreur et une erreur irrécupérable dans le journal.|  
|**Avertissement**|Écrire des messages d’avertissement, erreur et une erreur irrécupérable dans le journal.|  
|**Info**|Écrire des information, avertissement, messages d’erreur et erreur irrécupérable dans le journal.|  
|**Débogage**|Écrire tous les messages, y compris les messages, dans le journal de débogage.|  
  
**Chemin du fichier journal**  
Le chemin d’accès de fichier et le nom des fichiers journaux SSMA. Pour spécifier un nom différent, cliquez sur le chemin d’accès actuel, puis cliquez sur le bouton de navigation (**...** ) bouton.  
  
**Taille du fichier journal**  
La taille maximale du fichier journal en Ko. La taille minimale est de 10 Ko. La taille par défaut est 10 240 Ko.  
  
**Nombre total de fichiers journaux**  
Lorsqu’un journal se remplit, SSMA sera renommer le fichier journal et démarrer une nouvelle. À l’aide de ce paramètre, spécifiez le nombre maximal de fichiers journaux à conserver. La valeur minimale est 2.  
  
