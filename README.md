# mvvm-with-architecture-component
# 1. Project guidelines

## 1.1 Project Hierarchy

```
📦 app
┣ 📂 common
┣ 📂 config
┣ 📂 di
┣ 📂 domain
┃ ┣ 📂 repository
┃ ┃ ┗ 📜 AuthRepositoryImpl.kt
┃ ┗ 📂 usecase
┃   ┗ 📂 auth
┃     ┗ 📜 GetAuth.kt
┣ 📂 model // another pojo
┃ ┗ 📂 auth
┃   ┗ 📜 AuthModel.kt
┣ 📂 repository // Interface of repository
┃ ┗ 📜 Repository.kt
┣ 📂 ui
┃ ┗ 📂 auth
┗ 📂 util
  ┣ 📂 network
  ┣ 📂 database
  ┗ 📂 extension

component
┗ 📂 {CustomViewModule}

common
┣ 📂 data
┃  ┣ 📂 remote
┃  ┃ ┗ 📂 auth
┃  ┃   ┣ 📜 AuthService.kt
┃  ┃   ┣ 📜 AuthRequest.kt
┃  ┃   ┗ 📜 AuthResponse.kt
┃  ┗ 📂 local
┃    ┗ 📂 auth
┃      ┣ 📜 AuthDao.kt
┃      ┗ 📜 AuthEntity.kt
┣ 📂 di
┣ 📂 routable
┗ 📂 style
  ┗ 📂 res
    ┣ 📂 anim
    ┣ 📂 drawable
    ┣ 📂 font
    ┣ 📂 mipmap
    ┣ 📂 transition
    ┗ 📂 values
    
```

## 1.2 File naming

### 1.2.1 Class files
Class names are written in [PascalCase](http://en.wikipedia.org/wiki/CamelCase).

For classes that extend an Android component, the name of the class should end with the name of the component; for example: `SignInActivity`, `SignInFragment`, `ImageUploaderService`, `ChangePasswordDialog`.

### 1.2.2 Resources files

Resources file names are written in __snake_case__.

#### 1.2.2.1 Drawable files

Naming conventions for drawables:


| Asset Type   | Prefix            |		Example               |
|--------------| ------------------|-----------------------------|
| Button       | `btn_`	            | `btn_example.xml`    |
| Dialog       | `dialog_`         | `dialog_example.xml`          |
| Divider      | `divider_`        | `divider_example.xml`  |
| Icon         | `ic_`	            | `ic_example.xml`               |
| Menu         | `menu_	`           | `menu_example.xml`     |
| Notification | `notification_`	| `notification_example.xml`     |
| Tabs         | `tab_`            | `tab_example.xml`         |
| Background   | `bg_`            | `bg_example.xml`         |

Naming conventions for icons (taken from [Android iconography guidelines](http://developer.android.com/design/style/iconography.html)):

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

Naming conventions for selector states:

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |


#### 1.2.2.2 Layout files

Layout files should match the name of the Android components that they are intended for but moving the top level component name to the beginning. For example, if we are creating a layout for the `SignInActivity`, the name of the layout file should be `activity_sign_in.xml`.

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Bottom sheet fragment         | `SignUpBottomSheetFragment`       | `fragment_bottom_sheet_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout (a part of screen)   | ---                    | `view_stats_bar.xml`       |

#### XML component id naming
XML id are written in ___snake_case___

| Component        | id                     | Class                     | 
| ---------------- | ---------------------- | ---------------------- |
| ViewGroup (FrameLayout, LinearLayout, ...)        | `layout_exmple`  | |
| include          | `include_example`  | |
| View             | `view_example`  | |
| ImageView, ShapeableImageView  | `img_example` | |
| Button           | `btn_example`  | `com.google.android.material.button.MaterialButton` |
| RecyclerView     | `rv_example`  | |
| TextView         | `tv_example`  | |
| EditText, TextInputEditText, AutoCompleteTextView | `et_example`  | |
| TextInputLayout  | `layout_et_example` | `com.google.android.material.textfield.TextInputLayout` |
| RadioGroup, Radio  | `layout_rd_example`, `rd_example` | |
| ScrollView  | `sv_example` | `androidx.core.widget.NestedScrollView` |
| ViewPager2  | `vp_example` | `androidx.viewpager2.widget.ViewPager2` |
| CardView  | `cv_example` | `com.google.android.material.card.MaterialCardView` |
| Toolbar  | `tb_example` | `com.google.android.material.appbar.MaterialToolbar` |
| TabLayout  | `tl_example` | `com.google.android.material.tabs.TabLayout` |
| WebView  | `wv_example` | |
| BottomNavigationView  | `bn_example` | `com.google.android.material.bottomnavigation.BottomNavigationView` |


A slightly different case is when we are creating a layout that is going to be inflated by an `Adapter`, e.g to populate a `ListView`. In this case, the name of the layout should start with `item_`.

Note that there are cases where these rules will not be possible to apply. For example, when creating layout files that are intended to be part of other layouts. In this case you should use the prefix `partial_`.

#### 1.2.2.3 Menu files

Similar to layout files, menu files should match the name of the component. For example, if we are defining a menu file that is going to be used in the `UserActivity`, then the name of the file should be `activity_user.xml`

A good practice is to not include the word `menu` as part of the name because these files are already located in the `menu` directory.

#### 1.2.2.4 Values files

Resource files in the values folder should be __plural__, e.g. `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`
