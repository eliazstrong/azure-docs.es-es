---
title: 'Tutorial: Integración de Azure Active Directory con Opal | Microsoft Docs'
description: Aprenda a configurar el inicio de sesión único entre Azure Active Directory y Opal.
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: 434fc204-e9f9-4678-ad5f-054d621bb2f9
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/09/2018
ms.author: jeedes
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9878e120a3456383812cca44e054a48759f683a3
ms.sourcegitcommit: 301128ea7d883d432720c64238b0d28ebe9aed59
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56202849"
---
# <a name="tutorial-azure-active-directory-integration-with-opal"></a>Tutorial: Integración de Azure Active Directory con Opal

En este tutorial, aprenderá a integrar Opal con Azure Active Directory (Azure AD).

La integración de Opal con Azure AD le proporciona las siguientes ventajas:

- En Azure AD se puede controlar quién tiene acceso a Opal.
- Puede permitir que los usuarios inicien sesión automáticamente en Opal (inicio de sesión único) con sus cuentas de Azure AD.
- Puede administrar sus cuentas en una ubicación central: Azure Portal.

Si desea saber más sobre la integración de aplicaciones SaaS con Azure AD, consulte [¿Qué es el acceso a aplicaciones y el inicio de sesión único con Azure Active Directory?](../manage-apps/what-is-single-sign-on.md).

## <a name="prerequisites"></a>Requisitos previos

Para configurar la integración de Azure AD con Opal, necesita los siguientes elementos:

- Una suscripción de Azure AD
- Una suscripción habilitada para el inicio de sesión único en Opal

> [!NOTE]
> Para probar los pasos de este tutorial, no se recomienda el uso de un entorno de producción.

Para probar los pasos de este tutorial, debe seguir estas recomendaciones:

- No use el entorno de producción, salvo que sea necesario.
- Si no dispone de un entorno de prueba de Azure AD, puede [obtener una versión de prueba durante un mes](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Descripción del escenario
En este tutorial, puede probar el inicio de sesión único de Azure AD en un entorno de prueba. El escenario descrito en este tutorial consta de dos bloques de creación principales:

1. Adición de Opal desde la galería
1. Configuración y comprobación del inicio de sesión único de Azure AD

## <a name="adding-opal-from-the-gallery"></a>Adición de Opal desde la galería
Para configurar la integración de Opal en Azure AD, será preciso agregar Opal desde la galería a la lista de aplicaciones SaaS administradas.

**Para agregar Opal desde la galería, realice los pasos siguientes:**

1. En el panel de navegación izquierdo de **[Azure Portal](https://portal.azure.com)**, haga clic en el icono de **Azure Active Directory**. 

    ![Botón Azure Active Directory][1]

1. Vaya a **Aplicaciones empresariales**. A continuación, vaya a **Todas las aplicaciones**.

    ![Hoja Aplicaciones empresariales][2]
    
1. Para agregar una nueva aplicación, haga clic en el botón **Nueva aplicación** de la parte superior del cuadro de diálogo.

    ![Botón Nueva aplicación][3]

1. En el cuadro de búsqueda, escriba **Opal**, seleccione **Opal** en el panel de resultados y, luego, haga clic en el botón **Agregar** para agregar la aplicación.

    ![Opal en la lista de resultados](./media/opal-tutorial/tutorial_opal_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configuración y prueba del inicio de sesión único en Azure AD

En esta sección, podrá configurar y probar el inicio de sesión único de Azure AD con Opal con un usuario de prueba llamado "Britta Simon".

Para que el inicio de sesión único funcione, Azure AD debe saber cuál es el usuario homólogo de Opal para un usuario de Azure AD. Es decir, es necesario establecer una relación de vínculo entre un usuario de Azure AD y el usuario relacionado de Opal.

Para establecer la relación de vínculo, en Opal, asigne el valor de **nombre de usuario** de Azure AD como valor de **nombre de usuario**.

Para configurar y probar el inicio de sesión único de Azure AD con Opal, es preciso completar los siguientes bloques de creación:

1. **[Configuración del inicio de sesión único de Azure AD](#configure-azure-ad-single-sign-on)**: para que los usuarios puedan usar esta característica.
1. **[Creación de un usuario de prueba de Azure AD](#create-an-azure-ad-test-user)**, para probar el inicio de sesión único de Azure AD con Britta Simon.
1. **[Creación de un usuario de prueba de Opal](#create-an-opal-test-user)**: para tener un homólogo de Britta Simon en Opal que esté vinculado a la representación del usuario en Azure AD.
1. **[Asignación del usuario de prueba de Azure AD](#assign-the-azure-ad-test-user)**, para permitir que Britta Simon use el inicio de sesión único de Azure AD.
1. **[Prueba del inicio de sesión único](#test-single-sign-on)**: para comprobar si la configuración funciona.

### <a name="configure-azure-ad-single-sign-on"></a>Configuración del inicio de sesión único de Azure AD

En esta sección, habilitará el inicio de sesión único de Azure AD en Azure Portal y configurará el inicio de sesión único en la aplicación Opal.

**Para configurar el inicio de sesión único de Azure AD con Opal, realice los pasos siguientes:**

1. En Azure Portal, en la página de integración de la aplicación **Opal**, haga clic en **Inicio de sesión único**.

    ![Vínculo Configurar inicio de sesión único][4]

1. En el cuadro de diálogo **Inicio de sesión único**, en **Modo** seleccione **Inicio de sesión basado en SAML** para habilitar el inicio de sesión único.
 
    ![Cuadro de diálogo Inicio de sesión único](./media/opal-tutorial/tutorial_opal_samlbase.png)

1. En la sección **Dominio y direcciones URL de Opal**, lleve a cabo los pasos siguientes:

    ![Información de dominio y direcciones URL de inicio de sesión único de Opal](./media/opal-tutorial/tutorial_opal_url.png)

     a. En el cuadro de texto **Identificador**, escriba un valor: `Opal`

    b. En el cuadro de texto **URL de respuesta**, escriba una dirección URL con el siguiente patrón: `https://<subdomain>.ouropal.com/auth/saml/callback`.

    > [!NOTE] 
    > El valor de dirección URL de respuesta no es real. Actualícelo con la dirección URL de respuesta real. Póngase en contacto con el [equipo de soporte técnico de Opal](mailto:support@workwithopal.com) para obtener este valor.

1. La aplicación Opal espera las aserciones de SAML en un formato específico. Configure las siguientes notificaciones para esta aplicación. Puede administrar los valores de estos atributos en la sección **Atributos de usuario** de la página de integración de aplicaciones. La siguiente captura de pantalla le muestra un ejemplo de esto.
    
    ![Configurar el atributo de inicio de sesión único](./media/opal-tutorial/tutorial_opal_attribute.png)
    
1. En la sección **Atributos de usuario** del cuadro de diálogo **Inicio de sesión único**, configure el atributo token de SAML como muestra la imagen y siga estos pasos:
    
    | Nombre del atributo | Valor de atributo |
    | ------------------- | -------------------- |    
    | firstname           | user.givenname |
    | lastname        | user.surname |

     a. Haga clic en **Agregar atributo** para abrir el cuadro de diálogo **Agregar atributo**.

    ![Configurar la adición del inicio de sesión único](./media/opal-tutorial/tutorial_attribute_04.png)

    ![Configurar la adición del atributo del inicio de sesión único](./media/opal-tutorial/tutorial_attribute_05.png)

    b. En el cuadro de texto **Nombre**, escriba el nombre que se muestra para la fila.

    c. En la lista **Valor**, seleccione el atributo que se muestra para esa fila.

    d. Deje **Espacio de nombres** en blanco.
    
    e. Haga clic en **Aceptar**.
 
1. En la sección **Certificado de firma de SAML**, haga clic en **XML de metadatos** y luego guarde el archivo de metadatos en el equipo.

    ![Vínculo de descarga del certificado](./media/opal-tutorial/tutorial_opal_certificate.png) 

1. Haga clic en el botón **Guardar** .

    ![Botón Configurar inicio de sesión único](./media/opal-tutorial/tutorial_general_400.png) 

1. Para configurar el inicio de sesión único en **Opal**, necesita enviar el archivo **XML de metadatos** descargado al [equipo de soporte técnico de Opal](mailto:support@workwithopal.com). Dicho equipo lo configura para establecer la conexión de SSO de SAML correctamente en ambos lados.

> [!TIP]
> Ahora puede leer una versión resumida de estas instrucciones dentro de [Azure Portal](https://portal.azure.com) mientras configura la aplicación.  Después de agregar esta aplicación desde la sección **Active Directory > Aplicaciones empresariales**, simplemente haga clic en la pestaña **Inicio de sesión único** y acceda a la documentación insertada a través de la sección **Configuración** de la parte inferior. Puede leer más aquí sobre la característica de documentación insertada: [Documentación insertada de Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)

### <a name="create-an-azure-ad-test-user"></a>Creación de un usuario de prueba de Azure AD

El objetivo de esta sección es crear un usuario de prueba en Azure Portal llamado "Britta Simon".

   ![Creación de un usuario de prueba de Azure AD][100]

**Siga estos pasos para crear un usuario de prueba en Azure AD:**

1. En el panel izquierdo de Azure Portal, haga clic en el botón **Azure Active Directory**.

    ![Botón Azure Active Directory](./media/opal-tutorial/create_aaduser_01.png)

1. Para mostrar la lista de usuarios, vaya a **Usuarios y grupos** y, luego, haga clic en **Todos los usuarios**.

    ![Vínculos "Usuarios y grupos" y "Todos los usuarios"](./media/opal-tutorial/create_aaduser_02.png)

1. En la parte superior del cuadro de diálogo **Todos los usuarios**, haga clic en **Agregar** para abrir el cuadro de diálogo **Agregar**.

    ![Botón Agregar](./media/opal-tutorial/create_aaduser_03.png)

1. En el cuadro de diálogo **Usuario** , realice los pasos siguientes:

    ![Cuadro de diálogo Usuario](./media/opal-tutorial/create_aaduser_04.png)

     a. En el cuadro **Nombre**, escriba **BrittaSimon**.

    b. En el cuadro de texto **Nombre de usuario**, escriba la dirección de correo electrónico del usuario Britta Simon.

    c. Active la casilla **Mostrar contraseña** y, después, anote el valor que se muestra en el cuadro **Contraseña**.

    d. Haga clic en **Create**(Crear).
  
### <a name="create-an-opal-test-user"></a>Creación de un usuario de prueba de Opal

En esta sección, creará un usuario llamado Britta Simon en Opal. Trabaje con el  [equipo de soporte técnico de Opal](mailto:support@workwithopal.com)  para agregar los usuarios en la plataforma de Opal. Los usuarios se tienen que crear y activar antes de usar el inicio de sesión único. 

### <a name="assign-the-azure-ad-test-user"></a>Asignación del usuario de prueba de Azure AD

En esta sección, permitirá que Britta Simon use el inicio de sesión único de Azure concediéndole acceso a Opal.

![Asignación de rol de usuario][200] 

**Para asignar a Britta Simon a Opal, realice los pasos siguientes:**

1. En Azure Portal, abra la vista de aplicaciones, navegue a la vista de directorio y vaya a **Aplicaciones empresariales**. Luego haga clic en **Todas las aplicaciones**.

    ![Asignar usuario][201] 

1. En la lista de aplicaciones, seleccione **Opal**.

    ![Vínculo a Opal en la lista de aplicaciones](./media/opal-tutorial/tutorial_opal_app.png)  

1. En el menú de la izquierda, haga clic en **Usuarios y grupos**.

    ![Vínculo "Usuarios y grupos"][202]

1. Haga clic en el botón **Agregar**. Después, seleccione **Usuarios y grupos** en el cuadro de diálogo **Agregar asignación**.

    ![Panel Agregar asignación][203]

1. En el cuadro de diálogo **Usuarios y grupos**, seleccione **Britta Simon** en la lista de usuarios.

1. Haga clic en el botón **Seleccionar** del cuadro de diálogo **Usuarios y grupos**.

1. Haga clic en el botón **Asignar** del cuadro de diálogo **Agregar asignación**.
    
### <a name="test-single-sign-on"></a>Prueba de inicio de sesión único

En esta sección, probará la configuración de inicio de sesión único de Azure AD mediante el Panel de acceso.

Al hacer clic en el icono de Opal en el panel de acceso, debería iniciar sesión automáticamente en su aplicación Opal.
Para más información sobre el Panel de acceso, consulte la [introducción al Panel de acceso](../user-help/active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Recursos adicionales

* [Lista de tutoriales sobre cómo integrar aplicaciones SaaS con Azure Active Directory](tutorial-list.md)
* [¿Qué es el acceso a aplicaciones y el inicio de sesión único con Azure Active Directory?](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/opal-tutorial/tutorial_general_01.png
[2]: ./media/opal-tutorial/tutorial_general_02.png
[3]: ./media/opal-tutorial/tutorial_general_03.png
[4]: ./media/opal-tutorial/tutorial_general_04.png

[100]: ./media/opal-tutorial/tutorial_general_100.png

[200]: ./media/opal-tutorial/tutorial_general_200.png
[201]: ./media/opal-tutorial/tutorial_general_201.png
[202]: ./media/opal-tutorial/tutorial_general_202.png
[203]: ./media/opal-tutorial/tutorial_general_203.png

