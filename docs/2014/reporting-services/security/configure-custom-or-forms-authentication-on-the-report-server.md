---
title: Configurer l’authentification personnalisée ou par formulaire sur le serveur de rapports| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Forms authentication, configuring
- custom authentication [Reporting Services]
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8969e3202a9c58b46fac2116912e3d90474d7072
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59932536"
---
# <a name="configure-custom-or-forms-authentication-on-the-report-server"></a>Configurer l'authentification personnalisée ou par formulaire sur le serveur de rapports
  Reporting Services fournit une architecture extensible vous permettant d’incorporer des modules d'authentification personnalisés ou par formulaires. Vous pouvez envisager d'implémenter une extension d'authentification personnalisée si les spécifications de déploiement n'incluent pas la sécurité intégrée de Windows ou l’authentification de base. Le scénario d’utilisation de l'authentification personnalisée le plus courant est la prise en charge d’un accès Internet ou extranet à une application Web. Le remplacement de l’extension d’authentification Windows par défaut par une extension d'authentification personnalisée vous permet de mieux contrôler l'habilitation des utilisateurs externes à accéder au serveur de rapports.  
  
 En pratique, le déploiement d'une extension d'authentification personnalisée requiert plusieurs étapes, notamment la copie des assemblys et des fichiers d'application, la modification des fichiers de configuration et le test du système. Cette rubrique traite uniquement des paramètres d'authentification spécifiés dans les fichiers de configuration.  
  
> [!NOTE]  
>  La création d’une extension d’authentification personnalisée nécessite du code personnalisé et des compétences en matière de sécurité [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Si vous ne souhaitez pas créer de code pour une extension d'authentification personnalisée, vous pouvez utiliser des comptes et des groupes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory, mais vous devez réduire grandement l'étendue d'un déploiement de serveur de rapports. Pour plus d’informations sur l’authentification personnalisée, consultez [Implémentation d’une extension de sécurité](../extensions/security-extension/implementing-a-security-extension.md).  
  
 En outre, si vous souhaitez utiliser une authentification par formulaires ou une extension d'authentification personnalisée dans un environnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] intégré à un produit SharePoint, vous devez configurer le site SharePoint pour qu'il utilise la méthode d'authentification que vous choisissez. Pour plus d’informations sur la configuration de l’authentification dans SharePoint, consultez [Exemples d’authentification](https://go.microsoft.com/fwlink/?LinkId=115575) sur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Developer Network (MSDN).  
  
### <a name="to-configure-a-report-server-to-use-custom-authentication"></a>Pour configurer un serveur de rapports pour utiliser l'authentification personnalisée  
  
1.  Ouvrez RSReportServer.config dans un éditeur de texte.  
  
2.  Trouver <`Authentication`>.  
  
3.  Copiez la structure XML suivante :  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  Collez-la sur les entrées existantes de <`Authentication`>.  
  
     Notez que vous ne pouvez pas utiliser `Custom` avec d'autres types d'authentification.  
  
5.  Enregistrez le fichier.  
  
6.  Ouvrez le fichier Web.config du serveur de rapports. Par défaut, celui-ci se trouve dans le dossier \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer.  
  
7.  Recherchez `authentication mode` et affectez lui la valeur `Forms`.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  Recherchez `identity impersonate` et affectez-lui la valeur `False`.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. Ouvrez le fichier Web.config du Gestionnaire de rapports. Par défaut, celui-ci se trouve dans le dossier \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager.  
  
10. Recherchez `authentication mode` et affectez lui la valeur `Forms`.  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. Recherchez `identity impersonate` et affectez-lui la valeur `False`.  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. Ajouter la structure d’éléments `PassThroughCookies` au fichier de configuration. Pour plus d’informations, consultez [Configurer le Gestionnaire de rapports pour passer des cookies d’authentification personnalisée](configure-the-web-portal-to-pass-custom-authentication-cookies.md).  
  
13. Enregistrez le fichier.  
  
14. Si vous avez configuré un déploiement avec montée en puissance parallèle, répétez l’ensemble des étapes précédentes pour d'autres serveurs de rapports du déploiement.  
  
15. Redémarrez le serveur de rapports pour effacer toutes les sessions qui sont actuellement ouvertes.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une extension de sécurité](../extensions/security-extension/implementing-a-security-extension.md)   
 [Authentification avec le serveur de rapports](authentication-with-the-report-server.md)   
 [Fichier de Configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md)   
 [Configurer une authentification de base sur le serveur de rapports](configure-basic-authentication-on-the-report-server.md)   
 [Configurer une authentification Windows sur le serveur de rapports](configure-windows-authentication-on-the-report-server.md)  
  
  
