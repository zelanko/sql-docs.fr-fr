---
title: Configurer la Destination de fichier plat (SQL Server Assistant Importation et exportation) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.configureflatfiledest.f1
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: 93fbd5e9429d06e3f011f6f0aff03d76a3db9000
ms.contentlocale: fr-fr
ms.lasthandoff: 10/13/2017

---
# <a name="configure-flat-file-destination-sql-server-import-and-export-wizard"></a>Configurer la destination du fichier plat (Assistant Importation et Exportation SQL Server)
  Si vous avez sélectionné une destination de fichier plat, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] montre Assistant Importation et exportation **configurer la Destination de fichier plat** une fois que vous spécifiez que vous souhaitez copier une table ou une fois que vous spécifiez une requête. Dans cette page, vous spécifiez les options de mise en forme du fichier plat de destination. Si vous le souhaitez, vous pouvez passer en revue le mappage des colonnes et afficher un aperçu des exemples de données.  
  
## <a name="screen-shot-of-the-configure-flat-file-destination-page"></a>Capture d’écran de la page Configurer la destination du fichier plat  
 La capture d’écran suivante montre un exemple de la **configurer la Destination de fichier plat** page de l’Assistant.
 
 Dans cet exemple, l’utilisateur a spécifié les options suivantes pour créer un fichier (valeurs séparées par des virgules) de volume partagé de cluster classique.
-   **Délimiteur de ligne**. Chaque ligne de données dans la sortie se termine par un retour chariot-ligne combinaison de flux.
-   **Délimiteur de colonne**. Colonnes de données dans chaque ligne sont séparés par des virgules.

 ![Configurer la page de l’Assistant Importation et exportation de fichier plat](../../integration-services/import-export-data/media/flat-file.png)
  
## <a name="pick-a-source-table"></a>Choisissez une table source
 **Vue ou table source**  
-   Si vous avez spécifié dans une page précédente que vous voulez copier une table, sélectionnez la table source ou la vue dans la liste déroulante.
-   Si vous avez fourni une requête, `"Query"` est sélectionné et est la seule option.  

## <a name="specify-row-and-column-delimiters-for-the-output"></a>Spécifier des délimiteurs de lignes et de colonnes pour la sortie
 **Séparateur de lignes**  
 Sélectionnez dans la liste des délimiteurs pour séparer les lignes dans la sortie. Il n’existe aucune option pour spécifier un *personnalisé* séparateur de lignes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Délimiter les lignes avec une combinaison retour chariot-saut de ligne.|  
|**{CR}**|Délimiter les lignes avec un retour chariot.|  
|**{LF}**|Délimiter les lignes avec un saut de ligne.|  
|**Point-virgule {;}**|Délimiter les lignes avec un point-virgule.|  
|**Deux-points {:}**|Délimiter les lignes avec un signe deux-points.|  
|**Virgule {,}**|Délimiter les lignes avec une virgule.|  
|**Tabulation {t}**|Délimiter les lignes avec une tabulation.|  
|**Barre verticale {&#124;}**|Délimiter les lignes avec une barre verticale.|  
  
 **Délimiteur de colonne**  
 Sélectionnez dans la liste des séparateurs pour séparer les colonnes dans la sortie. Il n’existe aucune option pour spécifier un *personnalisé* délimiteur de colonne.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Délimiter les colonnes avec une combinaison retour chariot-saut de ligne.|  
|**{CR}**|Délimiter les colonnes avec un retour chariot.|  
|**{LF}**|Délimiter les colonnes avec un saut de ligne.|  
|**Point-virgule {;}**|Délimiter les colonnes avec un point-virgule.|  
|**Deux-points {:}**|Délimiter les colonnes avec un signe deux-points.|  
|**Virgule {,}**|Délimiter les colonnes avec une virgule.|  
|**Tabulation {t}**|Délimiter les colonnes avec une tabulation.|  
|**Barre verticale {&#124;}**|Délimiter les colonnes avec une barre verticale.|  

## <a name="optionally-review-column-mappings-and-preview-data"></a>Si vous le souhaitez, passez en revue les mappages de colonnes et afficher un aperçu des données

**Modifier les mappages**   
Si vous le souhaitez, cliquez sur **modifier les mappages** pour afficher les **mappages de colonnes** boîte de dialogue pour la table sélectionnée. Utilisez la boîte de dialogue **Mappage de colonnes** pour effectuer les opérations suivantes.
-   Passer en revue le mappage des colonnes entre la source et la destination.
-   Vous pouvez copier uniquement un sous-ensemble de colonnes en sélectionnant **ignorer** pour les colonnes que vous souhaitez ignorer.

Pour plus d’informations, consultez [Mappages de colonnes](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  

**Aperçu**  
Si vous le souhaitez, cliquez sur **aperçu** pour afficher un aperçu jusqu'à 200 lignes de données d’exemple dans le **aperçu des données** boîte de dialogue. Cela confirme que l’Assistant va copier les données que vous souhaitez copier. Pour plus d’informations, consultez [Aperçu des données](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).  
  
Après avoir affiché un aperçu des données, vous souhaiterez peut-être modifier les options que vous avez sélectionnées dans les pages précédentes de l’Assistant. Pour effectuer ces modifications, retournez dans la page **Configurer la destination du fichier plat** , puis cliquez sur **Précédent** pour revenir aux pages précédentes où vous pouvez modifier vos sélections.  

## <a name="whats-next"></a>Étape suivante  
 Après avoir spécifié les options de mise en forme pour le fichier plat de destination, la page suivante est **Enregistrer et exécuter le package**. Dans cette page, vous spécifiez si vous souhaitez exécuter l’opération immédiatement. Selon votre configuration, vous pouvez également être en mesure d’enregistrer vos paramètres en tant qu’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package afin de le personnaliser et à le réutiliser plus tard. Pour plus d’informations, consultez [Enregistrer et exécuter le package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  


