---
title: "Configurer la destination du fichier plat (Assistant Importation et Exportation SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.configureflatfiledest.f1"
ms.assetid: 318e8da0-37d3-46cd-943a-fc5d66aad93a
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Configurer la destination du fichier plat (Assistant Importation et Exportation SQL Server)
  Si vous avez sélectionné une destination de fichier plat, l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche **Configurer la destination du fichier plat** une fois que vous avez spécifié une table à copier ou que vous avez fourni une requête. Dans cette page, vous spécifiez les options de mise en forme du fichier plat de destination. Si vous le souhaitez, vous pouvez passer en revue le mappage des colonnes et afficher un aperçu des exemples de données.  
  
## <a name="screen-shot-of-the-configure-flat-file-destination-page"></a>Capture d’écran de la page Configurer la destination du fichier plat  
 La capture d’écran suivante montre la page **Configurer la destination du fichier plat** de l’Assistant.
 
 Dans cet exemple, l’utilisateur souhaite créer un fichier CSV standard (valeurs séparées par une virgule), c’est-à-dire terminer chaque ligne de données dans la sortie par une combinaison retour chariot-saut de ligne, et séparer les colonnes de données sur chaque ligne par une virgule.

 ![Configure flat file page of the Import and Export Wizard](../../integration-services/import-export-data/media/flat-file.png "Configure flat file page of the Import and Export Wizard")  
  
## <a name="pick-a-source-table"></a>Choisissez une table source. 
 **Vue ou table source**  
 Sélectionnez la vue ou table source.  

## <a name="specify-the-row-and-column-delimiters"></a>Spécifier les délimiteurs de ligne et de colonne
 **Délimiteur de ligne**  
 Effectuez une sélection dans la liste des délimiteurs de lignes. Il n’existe aucune option pour spécifier un délimiteur de ligne personnalisé.  
  
|Valeur| Description|  
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
 Effectuez une sélection dans la liste des délimiteurs de colonnes. Il n’existe aucune option pour spécifier un délimiteur de colonne personnalisé.  
  
|Valeur| Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Délimiter les colonnes avec une combinaison retour chariot-saut de ligne.|  
|**{CR}**|Délimiter les colonnes avec un retour chariot.|  
|**{LF}**|Délimiter les colonnes avec un saut de ligne.|  
|**Point-virgule {;}**|Délimiter les colonnes avec un point-virgule.|  
|**Deux-points {:}**|Délimiter les colonnes avec un signe deux-points.|  
|**Virgule {,}**|Délimiter les colonnes avec une virgule.|  
|**Tabulation {t}**|Délimiter les colonnes avec une tabulation.|  
|**Barre verticale {&#124;}**|Délimiter les colonnes avec une barre verticale.|  

## <a name="optionally-edit-column-mappings-and-preview-sample-data"></a>Vous pouvez éventuellement modifier les mappages de colonnes et afficher un aperçu des exemples de données

**Modifier les mappages**   
Cliquez éventuellement sur **Modifier les mappages** pour afficher la boîte de dialogue **Mappage de colonnes** pour la table sélectionnée. Utilisez la boîte de dialogue **Mappage de colonnes** pour effectuer les opérations suivantes.
-   Passer en revue le mappage des colonnes entre la source et la destination.
-   Vous pouvez copier uniquement un sous-ensemble de colonnes en sélectionnant **ignorer** pour les colonnes que vous souhaitez ignorer.

Pour plus d’informations, consultez [Mappages de colonnes](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  

**Aperçu**  
Cliquez éventuellement sur **Aperçu** pour afficher un aperçu de 200 lignes d’exemples de données maximum dans la boîte de dialogue **Aperçu des données**. Cela confirme que l’Assistant va copier les données que vous souhaitez copier. Pour plus d’informations, consultez [Aperçu des données](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).  
  
Après avoir affiché un aperçu des données, vous souhaiterez peut-être modifier les options que vous avez sélectionnées dans les pages précédentes de l’Assistant. Pour effectuer ces modifications, retournez dans la page **Configurer la destination du fichier plat**, puis cliquez sur **Précédent** pour revenir aux pages précédentes où vous pouvez modifier vos sélections.  

## <a name="whats-next"></a>Étape suivante  
 Après avoir spécifié les options de mise en forme pour le fichier plat de destination, la page suivante est **Enregistrer et exécuter le package**. Dans cette page, vous spécifiez si vous souhaitez exécuter l’opération immédiatement. Selon votre configuration, vous pouvez également être en mesure d’enregistrer le package [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] créé par l’Assistant pour le personnaliser et le réutiliser ultérieurement. Pour plus d’informations, consultez [Enregistrer et exécuter le package](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  
