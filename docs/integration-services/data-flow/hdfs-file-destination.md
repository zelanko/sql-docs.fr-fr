---
title: Destination du fichier HDFS | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfiledest.f1
ms.assetid: 4338ce9f-c077-4301-aca5-47ed070ec94d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 418921c7ce0f37cbbf7953f6b8023a717f8ae54b
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65726778"
---
# <a name="hdfs-file-destination"></a>HDFS File Destination

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Le composant HDFS File Destination permet à un package SSIS d’écrire des données dans un fichier HDFS. Les formats de fichier pris en charge sont les formats texte, Avro et ORC.

 Pour configurer HDFS File Destination, opérez un glisser-déplacer de HDFS File Source vers le concepteur de flux de données, puis double-cliquez sur le composant pour ouvrir l’éditeur.

 ![Éditeur de la destination du fichier HDFS](../../integration-services/data-flow/media/hdfs-file-dest.png "Éditeur de la destination du fichier HDFS")

## <a name="options"></a>Options
 Configurez les options suivantes sur l’onglet **General (Général)** de la boîte de dialogue **Hadoop File Destination Editor (Éditeur de destination de fichiers Hadoop)** .

|Champ|Description|
|-----------|-----------------|
|**Connexion Hadoop**|Spécifiez un gestionnaire de connexions Hadoop existant ou créez-en un. Ce gestionnaire de connexions indique où se trouvent les fichiers HDFS.|
|**Chemin d'accès au fichier**|Spécifiez le nom du fichier HDFS.|
|**Format du fichier**|Spécifiez le format du fichier HDFS. Les options disponibles sont Texte, Avro et ORC.|
|**Caractère séparateur de colonnes**|Si vous avez sélectionné le format Texte, spécifiez le caractère délimiteur de colonne.|
|**Noms de colonnes dans la première ligne de données**|Si vous avez sélectionné le format Texte, indiquez si la première ligne du fichier contient les noms de colonnes.|

 Après avoir configuré ces options, sélectionnez l’onglet **Colonnes** pour mapper les colonnes source aux colonnes de destination dans le flux de données.

::: moniker range=">= sql-server-ver15"

## <a name="prerequisite-for-orc-file-format"></a>Prérequis pour le format de fichier ORC
Java est nécessaire pour utiliser le format de fichier ORC.
L’architecture (32/64 bits) de la build Java doit correspondre à celle du runtime SSIS à utiliser.
Les builds Java suivantes ont été testées.

- [Zulu OpenJDK 8u192](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Oracle Java SE Runtime Environment 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

### <a name="set-up-zulus-openjdk"></a>Configurer Zulu OpenJDK
1. Téléchargez et extrayez le package compressé d’installation.
2. À partir de l’invite de commandes, exécutez `sysdm.cpl`.
3. Sous l’onglet **Avancé**, sélectionnez **Variables d’environnement**.
4. Sous la section **Variables système**, sélectionnez **Nouveau**.
5. Entrez `JAVA_HOME` pour le **Nom de la variable**.
6. Sélectionnez **Parcourir les répertoires**, accédez au dossier extrait et sélectionnez le sous-dossier `jre`.
   Sélectionnez ensuite **OK** et la **valeur de la variable** est automatiquement renseignée.
7. Sélectionnez **OK** pour fermer la boîte de dialogue **Nouvelle Variable système**.
8. Sélectionnez **OK** pour fermer la boîte de dialogue **Variables d’environnement**.
9. Sélectionnez **OK** pour fermer la boîte de dialogue **Propriétés du système**.

### <a name="set-up-oracles-java-se-runtime-environment"></a>Configurer Oracle Java SE Runtime Environment
1. Téléchargez et exécutez le programme d’installation.
2. Suivez les instructions du programme d’installation pour terminer l’installation.

::: moniker-end

## <a name="see-also"></a> Voir aussi
[Gestionnaire de connexions Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)  
[Source de fichier HDFS](../../integration-services/data-flow/hdfs-file-source.md)
