---
title: Flexible File Source | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpextfilesrc.f1
- sql14.dts.designer.afpextfilesrc.f1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3e396e40f30571969b347c464687321b3b038212
ms.sourcegitcommit: fa2afe8e6aec51e295f55f8cc6ad3e7c6b52e042
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462534"
---
# <a name="flexible-file-source"></a>Source de fichier flexible

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Le composant **Flexible File Source** permet à un package SSIS de lire des données à partir de divers services de stockage pris en charge.
Les services de stockage actuellement pris en charge sont :

- [Stockage Blob Azure](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)
  
Pour afficher l’éditeur Flexible File Source, faites glisser **Flexible File Source** sur le concepteur de flux de données et double-cliquez dessus pour ouvrir l’éditeur.
  
**Flexible File Source** est un composant du [Feature Pack SQL Server Integration Services (SSIS) pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
Les propriétés suivantes sont disponibles sur l’**éditeur Flexible File Source**.

- **File Connection Manager Type** (Type du gestionnaire de connexions) : spécifie le type de gestionnaire de connexions source. Choisissez ensuite un gestionnaire existant du type spécifié ou créez-en un.
- **Folder Path (Chemin du dossier) :** spécifie le chemin du dossier source.
- **Nom de fichier :** spécifie le nom du fichier source.
- **File Format (Format du fichier) :** spécifie le format du fichier source. Les formats pris en charge sont **Text**, **Avro**, **ORC** et **Parquet**.
- **Column delimiter character (Caractère séparateur de colonnes) :** spécifie le caractère utilisé comme séparateur de colonnes (les délimiteurs à plusieurs caractères ne sont pas pris en charge).
- **First row as the column name (Première ligne comme nom de colonne) :** spécifie s’il faut considérer la première ligne comme un nom de colonne.
- **Decompress the file (Décompresser le fichier) :** spécifie s’il faut décompresser le fichier source.
- **Compression Type (Type de compression) :** spécifie le format de compression du fichier source. Les formats pris en charge sont **GZIP**, **DEFLATE** et **BZIP2**.
  
Les propriétés suivantes sont disponibles sur l’**éditeur avancé**.

- **rowDelimiter :** caractère utilisé pour séparer les lignes dans un fichier. Un seul caractère est autorisé. La valeur **par défaut** est \r\n.
- **escapeChar :** caractère spécial utilisé pour échapper un délimiteur de colonne dans le contenu du fichier d’entrée. Vous ne pouvez pas spécifier à la fois escapeChar et quoteChar pour une table. Un seul caractère est autorisé. Pas de valeur par défaut.
- **quoteChar :** caractère utilisé pour mettre entre guillemets une valeur de chaîne. Les délimiteurs de colonnes et de lignes à l’intérieur des guillemets seraient considérés comme faisant partie de la valeur de chaîne. Cette propriété s’applique aux jeux de données d’entrée et de sortie. Vous ne pouvez pas spécifier à la fois escapeChar et quoteChar pour une table. Un seul caractère est autorisé. Pas de valeur par défaut.
- **nullValue :** un ou plusieurs caractères utilisés pour représenter une valeur Null. La valeur **par défaut** est \N.
- **encodingName :** spécifiez le nom du codage. Voir la propriété [Encoding.EncodingName](https://docs.microsoft.com/en-us/dotnet/api/system.text.encoding?redirectedfrom=MSDN&view=netframework-4.8).
- **skipLineCount :**  indique le nombre de lignes non vides à ignorer lors de la lecture des données à partir des fichiers d’entrée. Si skipLineCount et firstRowAsHeader sont spécifiés, les lignes sont d’abord ignorées, puis les informations d’en-têtes sont lues à partir du fichier d’entrée.
- **treatEmptyAsNull :** spécifie s’il faut traiter une chaîne Null ou vide comme une valeur Null lors de la lecture des données à partir d’un fichier d’entrée. La valeur **par défaut** est True.

Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.

**Prérequis pour le format de fichier ORC/Parquet**

Java est nécessaire pour utiliser le format de fichier ORC/Parquet.
L’architecture (32/64 bits) de la build Java doit correspondre à celle du runtime SSIS à utiliser.
Les builds Java suivantes ont été testées.

- [Zulu OpenJDK 8u192](https://www.azul.com/downloads/zulu/zulu-windows/)
- [Oracle Java SE Runtime Environment 8u192](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html)

**Configurer Zulu OpenJDK**

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

**Configurer Oracle Java SE Runtime Environment**

1. Téléchargez et exécutez le programme d’installation.
2. Suivez les instructions du programme d’installation pour terminer l’installation.
