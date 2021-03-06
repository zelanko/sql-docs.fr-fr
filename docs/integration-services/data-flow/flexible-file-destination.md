---
description: Destination de fichier flexible
title: Flexible File Destination | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpextfiledest.f1
- sql14.dts.designer.afpextfiledest.f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 253bd5f8accf3e2fd9fc28dcaa535bea6f736316
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96127164"
---
# <a name="flexible-file-destination"></a>Destination de fichier flexible

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Le composant **Flexible File Destination** permet à un package SSIS d’écrire des données vers divers services de stockage pris en charge.

Les services de stockage actuellement pris en charge sont :

- [Stockage Blob Azure](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction)
   
Faites glisser le composant **Flexible File Destination** vers le concepteur de flux de données et double-cliquez dessus pour visualiser l’éditeur.
  
**Flexible File Destination** est un composant du [Feature Pack SQL Server Integration Services (SSIS) pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  

Les propriétés suivantes sont disponibles sur l’**éditeur Flexible File Destination**.

- **File Connection Manager Type** (Type du gestionnaire de connexions) : spécifie le type de gestionnaire de connexions source. Choisissez ensuite un gestionnaire existant du type spécifié ou créez-en un.
- **Folder Path (Chemin du dossier) :** spécifie le chemin du dossier de destination.
- **Nom de fichier :** spécifie le nom du fichier de destination.
- **File Format (Format du fichier) :** spécifie le format du fichier de destination. Les formats pris en charge sont **Text**, **Avro**, **ORC** et **Parquet**. Vous devez utiliser Java pour ORC/Parquet. Cliquez [ici](../../integration-services/azure-feature-pack-for-integration-services-ssis.md#dependency-on-java) pour obtenir des détails.
- **Column delimiter character (Caractère séparateur de colonnes) :** spécifie le caractère à utiliser comme séparateur de colonnes (les délimiteurs à plusieurs caractères ne sont pas pris en charge).
- **First row as the column name (Première ligne comme nom de colonne) :** spécifie s’il faut écrire des noms de colonnes sur la première ligne.
- **Compress the file (Compresser le fichier) :** spécifie s’il faut compresser le fichier.
- **Compression Type (Type de compression) :** spécifie le format de compression à utiliser. Les formats pris en charge sont **GZIP**, **DEFLATE** et **BZIP2**.
- **Compression Level (Niveau de compression) :** spécifie le niveau de compression à utiliser.

Les propriétés suivantes sont disponibles sur l’**éditeur avancé**.

- **rowDelimiter :** caractère utilisé pour séparer les lignes dans un fichier. Un seul caractère est autorisé. La valeur **par défaut** est \r\n.
- **escapeChar :** caractère spécial utilisé pour échapper un délimiteur de colonne dans le contenu du fichier d’entrée. Vous ne pouvez pas spécifier à la fois escapeChar et quoteChar pour une table. Un seul caractère est autorisé. Pas de valeur par défaut.
- **quoteChar :** caractère utilisé pour mettre entre guillemets une valeur de chaîne. Les délimiteurs de colonnes et de lignes à l’intérieur des guillemets seraient considérés comme faisant partie de la valeur de chaîne. Cette propriété s’applique aux jeux de données d’entrée et de sortie. Vous ne pouvez pas spécifier à la fois escapeChar et quoteChar pour une table. Un seul caractère est autorisé. Pas de valeur par défaut.
- **nullValue :** un ou plusieurs caractères utilisés pour représenter une valeur Null. La valeur **par défaut** est \N.
- **encodingName :** spécifiez le nom du codage. Voir la propriété [Encoding.EncodingName](/dotnet/api/system.text.encoding?view=netframework-4.8).
- **skipLineCount :**  indique le nombre de lignes non vides à ignorer lors de la lecture des données à partir des fichiers d’entrée. Si skipLineCount et firstRowAsHeader sont spécifiés, les lignes sont d’abord ignorées, puis les informations d’en-têtes sont lues à partir du fichier d’entrée.
- **treatEmptyAsNull :** spécifie s’il faut traiter une chaîne Null ou vide comme une valeur Null lors de la lecture des données à partir d’un fichier d’entrée. La valeur **par défaut** est True.

Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.

**Remarques sur la configuration des autorisations du principal de service**

Pour que la **connexion de test** fonctionne (soit le stockage d’objets blob, soit Data Lake Storage Gen2), le principal de service doit disposer au moins du rôle **Lecteur des données Blob du stockage** pour le compte de stockage.
Cette opération s’effectue à l’aide de [RBAC](/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).

Pour le stockage d’objets blob, l’autorisation d’écriture est accordée en affectant au moins le rôle **Contributeur aux données Blob du stockage**.

Pour Data Lake Storage Gen2, l’autorisation est déterminée à la fois par RBAC et par des [listes des contrôles d’accès (ACL)](/azure/storage/blobs/data-lake-storage-how-to-set-permissions-storage-explorer).
Faites attention à ce que les listes de contrôle d’accès soient configurées à l’aide de l’ID d’objet (OID) du principal de service pour l’inscription d’application, comme indiqué [ici](/azure/storage/blobs/data-lake-storage-access-control#how-do-i-set-acls-correctly-for-a-service-principal).
Cet ID diffère de l’ID d’application (client) utilisé avec la configuration RBAC.
Quand un principal de sécurité reçoit des autorisations sur les données RBAC par le biais d’un rôle intégré ou personnalisé, ces autorisations sont évaluées en premier lors de l’autorisation d’une demande.
Si l’opération demandée est autorisée par les attributions RBAC du principal de sécurité, l’autorisation est immédiatement résolue et aucune vérification de liste de contrôle d’accès supplémentaire n’est effectuée.
Sinon, si le principal de sécurité n’a pas d’attribution RBAC ou si l’opération de la demande ne correspond pas à l’autorisation affectée, les vérifications de liste de contrôle d’accès sont effectuées pour déterminer si le principal de sécurité est autorisé à effectuer l’opération demandée.
Pour l’autorisation d’écriture, accordez au moins l’autorisation d’**Exécution** à partir du système de fichiers récepteur, ainsi que l’autorisation d’**Écriture** pour le dossier récepteur.
Vous pouvez également accorder au moins le rôle **Contributeur aux données Blob du stockage** avec RBAC.
Pour plus d’informations, consultez [cet](/azure/storage/blobs/data-lake-storage-access-control) article.