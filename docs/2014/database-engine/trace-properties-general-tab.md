---
title: Propriétés de trace (onglet Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.general.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: 25227268-143b-477e-aac9-8268bcaf2078
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 573c8d13b9a7431c33d8c3b104712a2bf31b3fbf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66089531"
---
# <a name="trace-properties-general-tab"></a>Propriétés de la trace (onglet Général)
  Utilisez l’onglet **Général** de la boîte de dialogue **Propriétés de la trace** pour consulter ou spécifier les propriétés d’une trace.  
  
## <a name="options"></a>Options  
 **Nom de la trace**  
 Spécifiez le nom de la trace.  
  
 **Nom du fournisseur de trace**  
 Affiche le nom de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui va être tracée. Ce champ est automatiquement rempli avec le nom du serveur que vous avez spécifié lorsque vous vous êtes connecté. Pour modifier le nom du fournisseur de la trace, cliquez sur **Annuler** pour fermer la boîte de dialogue et démarrez une nouvelle trace.  
  
 **Type de fournisseur de trace**  
 Affiche le type de serveur qui fournit la trace. Le champ **Type de fournisseur de trace** est rempli automatiquement par le fichier de définition de trace. Vous ne pouvez pas modifier ce champ.  
  
 **version**  
 Affiche la version du serveur qui fournit la trace. Le champ **Version** est rempli automatiquement par le fichier de définition de trace. Vous ne pouvez pas modifier ce champ.  
  
 **Utiliser le modèle**  
 Sélectionnez un modèle dans le répertoire des modèles. Le répertoire contient les modèles par défaut et tous les modèles définis par l'utilisateur créés pour le type de fournisseur de trace actuel.  
  
 **Enregistrer dans le fichier**  
 Cette option permet de capturer les données de trace dans un fichier .trc. L'enregistrement des données de trace vous permet de consulter et d'analyser ces données plus tard.  
  
 **Définir la taille de fichier maximale (Mo)**  
 Si vous décidez d'enregistrer les données de trace dans un fichier, vous devez indiquer la taille maximale de ce fichier. La valeur par défaut est 5 mégaoctets (Mo). La taille maximale est uniquement limitée par le système de fichiers (NTFS, FAT) dans lequel le fichier est enregistré.  
  
 \<Graphique > **enregistrer en tant que**  
 Une fois que vous avez choisi d'enregistrer les données dans un fichier, vous pouvez sélectionner cette icône pour modifier le nom du fichier.  
  
 **Activer la substitution de fichier**  
 Sélectionnez cette option pour autoriser la création de fichiers supplémentaires pour accueillir les données de trace lorsque la taille de fichier maximale est atteinte. Chaque nouveau nom de fichier correspond au nom du fichier .trc d'origine numéroté séquentiellement. Par exemple, une fois qu’il a atteint la taille de fichier maximale, **NouvelleTrace.trc** se ferme et un nouveau fichier, **NouvelleTrace_1.trc**, s’ouvre, suivi par **NouvelleTrace_2.trc**, et ainsi de suite. La substitution de fichier est activée par défaut lorsque vous enregistrez une trace dans un fichier.  
  
 **Le serveur traite les données de trace**  
 Cette option indique que le serveur exécutant la trace doit traiter les données de trace. L'utilisation de cette option réduit la charge de travail générée par le traçage. Lorsque cette option est activée, aucun événement n'est ignoré même en cas de charge importante. Si cette option n'est pas activée, c'est le Générateur de profils SQL Server qui traite les événements et il se peut que certains ne soient pas tracés en cas de conditions difficiles.  
  
 **Enregistrer dans la table**  
 Cette option permet de capturer les données de trace dans une table de base de données. L'enregistrement des données de trace vous permet de consulter et d'analyser ces données plus tard. Ce choix peut néanmoins provoquer un surcroît de charge important sur le serveur où les données de trace sont enregistrées. Si possible, n'enregistrez pas la table de trace sur le serveur qui est tracé.  
  
 \<Graphique > **Table de Destination**  
 Une fois que vous avez choisi d'enregistrer les données de trace dans une table de base de données, vous pouvez sélectionner cette icône pour modifier le nom de la table.  
  
 **Définir le nombre de lignes maximal (en milliers)**  
 Spécifiez le nombre maximal de lignes pour l'enregistrement des données. La valeur par défaut est 1000 lignes.  
  
 **Activer l'heure d'arrêt de la trace**  
 Définissez la date et l'heure auxquelles la trace doit s'arrêter et se fermer.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
