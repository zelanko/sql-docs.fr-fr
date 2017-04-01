---
title: "Bo&#238;te de dialogue Propri&#233;t&#233;s du catalogue | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.iscreatecatalog.f1"
  - "sql13.ssis.ssms.iscatalogprop.general.f1"
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Bo&#238;te de dialogue Propri&#233;t&#233;s du catalogue
  Utilisez la boîte de dialogue Propriétés du catalogue pour configurer le catalogue SSISDB. Les propriétés de catalogue définissent la façon dont les données sensibles sont chiffrées, la façon dont les opérations et les données du contrôle de version du projet sont conservées et le délai d'attente des opérations de validation. Le catalogue SSISDB est une base de données qui représente le point d’administration et de stockage central pour les projets, les packages, les paramètres et les environnements [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Vous pouvez également consulter les propriétés de catalogue dans la vue catalog.catalog_property et les définir à l'aide de la procédure stockée catalog.configure_catalog. Pour plus d’informations, consultez [catalog.catalog_properties &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) et [catalog.configure_catalog &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 Pour plus d’informations sur la façon de créer le catalogue SSISDB, consultez [Créer le catalogue SSIS](../../integration-services/service/create-the-ssis-catalog.md).  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrez la boîte de dialogue Propriétés du catalogue.](#open_dialog)  
  
-   [Configurer les options](#options)  
  
##  <a name="open_dialog"></a> Ouvrez la boîte de dialogue Propriétés du catalogue.  
  
1.  Ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Connectez-vous au moteur de base de données Microsoft SQL Server.  
  
3.  Dans l’Explorateur d’objets, développez le nœud **Integration Services**, cliquez avec le bouton droit sur **SSISDB**, puis cliquez sur **Propriétés**.  
  
##  <a name="options"></a> Configurer les options  
  
### Options  
 Le tableau décrit certaines propriétés de la boîte de dialogue et les propriétés correspondantes dans la vue catalog.catalog_property.  
  
|Nom de la propriété (boîte de dialogue Propriétés du catalogue)|Nom de la propriété (vue catalog.catalog_property)|Description|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|Nom de l'algorithme de chiffrement|ENCRYPTION_CLEANUP_ENABLED|Spécifie le type de chiffrement utilisé pour chiffrer les valeurs des paramètres sensibles dans le catalogue. Les valeurs possibles sont les suivantes :<br /><br /> DES<br /><br /> TRIPLE_DES<br /><br /> TRIPLE_DES_3KEY<br /><br /> DESPX<br /><br /> AES_128<br /><br /> AES_192<br /><br /> AES_256 (par défaut)|  
|Délai d'attente de validation (secondes)|VALIDATION_TIMEOUT|Spécifiez le nombre maximum de secondes qu'une validation de projet ou qu'une validation de package peut mettre pour s'exécuter avant qu'elle ne soit arrêtée. La valeur par défaut est 300 secondes.<br /><br /> La validation est une opération asynchrone. Plus le projet ou le package est gros, plus la validation prendra du temps.<br /><br /> Pour plus d’informations sur la validation des projets et des packages, consultez [Types de données Integration Services dans les expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).|  
|Nettoyer les journaux régulièrement|OPERATION_CLEANUP_ENABLED|Définissez la propriété sur True pour indiquer que le travail de l'Agent SQL Server, à savoir le nettoyage des opérations, doit être exécuté. Sinon, définissez la propriété sur False.|  
|Période de rétention (jours)|RETENTION_WINDOW|Spécifiez l'âge maximal des données opérationnelles autorisées (en jours). Les données qui sont plus anciennes que le nombre de jours spécifié seront supprimés par le travail de l'agent SQL, à savoir le nettoyage des opérations.|  
|Nombre maximal de versions par projet|MAX_PROJECT_VERSIONS|Spécifiez combien de versions d'un projet seront stockées dans le catalogue. Les versions antérieures des projets qui dépassent le nombre autorisé maximum seront supprimées lorsque le travail de nettoyage sera exécuté.|  
  
  