---
title: Destination Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSDEST.F1
- sql14.dts.designer.afpadlsdest.f1
ms.assetid: 4c4f504f-dd2b-42c5-8a20-1a8ad9a5d632
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d934cafef262f5c07b5eeac95d65abd776d8bb35
ms.sourcegitcommit: fc0eb955b41c9c508a1fe550eb5421c05fbf11b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66403038"
---
# <a name="azure-data-lake-store-destination"></a>Destination Azure Data Lake Store

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Le composant **Destination Azure Data Lake Store** permet à un package SSIS d’écrire des données dans Azure Data Lake Store. Les formats de fichier pris en charge sont : Text, Avro et ORC. 
  
 **Destination Azure Data Lake Store** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
 
> [!NOTE]
> Pour que le gestionnaire de connexions Azure Data Lake Store et les composants qui l’utilisent, notamment la source Azure Data Lake Store et la destination Azure Data Lake Store, puissent se connecter aux services, veillez à télécharger la dernière version du Feature Pack Azure [ici](https://www.microsoft.com/download/details.aspx?id=49492). 

## <a name="configure-the-azure-data-lake-store-destination"></a>Configurer la destination Azure Data Lake Store  
1. Faites glisser le composant **Destination Azure Data Lake Store** vers le concepteur de flux de données et double-cliquez dessus pour visualiser l’éditeur.  

2.  Dans le champ **Gestionnaire de connexions Azure Data Lake Store** , spécifiez un gestionnaire de connexions Azure Data Lake Store existant ou créez-en un qui fait référence à un service Azure Data Lake Store.  
  
    1.  Dans le champ **Chemin du fichier** , spécifiez le nom du fichier où vous souhaitez écrire des données. Si ce fichier existe déjà, son contenu est remplacé.  
  
    2.  Dans le champ **Format de fichier** , spécifiez le format de fichier à utiliser.  
  
       Si le format de fichier est le format texte, vous devez renseigner le champ **Délimiteur de colonne** . Sélectionnez également l’option **Noms de colonne dans la première ligne de données** si la première ligne du fichier contient des noms de colonne.  

       Si le format du fichier est ORC, vous devez installer Java Runtime Environment (JRE) pour la plateforme appropriée.
  
3.  Après avoir spécifié les informations de connexion, basculez vers la page **Colonnes** pour mapper les colonnes sources sur les colonnes de destination du flux de données SSIS.  

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