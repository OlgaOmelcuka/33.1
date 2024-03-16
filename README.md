# 33.1 

def search_regisr(self): # метод поиска гипепссылки "Зарегистрироваться" и 
  нажатие на нее
  sarch_register =vself.drver.find_element(*self.register)
  actions = ActionChains(self.driver)
  actions.scroll_to_element(search_rester)
  actions.click(search_register)
  actions.perform()
  

class myAuth():
 load_dotenv()

  valid_email = os.getent("valid_email")
  valid_password = os.getenv("valid_password")
  valid_phone = os.getenv("valid_phone")

""" Насройка веб браузера силениум страница авторизации пользователя"""
def test_x():
browser = webdriver.Chrome()
browser = set_window_size(1200, 800)
browser.get ("https://d2c.passport.rt.ru/auth/realms/d2c/protocol/openid-connect/auth?client_id=account_)
pole_phone = brwser.find_element(By.XPATH, '//*[@id="page-right"]/div/div/div/form/div[1]/div[2]/div/
pole_phone.clean()
po_phone.send_keys(MyAuth.valid_phone)


TC-007 (авторизация по зарегистрированному номеру телефона)
def tet_auth_re_phone(selenium)
  form = Authform(selenium)
  # вводим номер телефона и пароль
  form.username.send_keys(valid_number)
  form.password.send_keys(valid_paaword)
  sleep(5)
  form.btn_click()

  assert fom.get_current_url =='https://b2c.pasport.rt.ru/auth/realms/b2c/protocol/openid-connect/' \
'āuthclient_id=account_b2cqredirect_uri=https://b2c.passport.rt.ru/account_b2c/' \lginQresponse_type=codeqscode=oenidQstate=d0a2a0b6-eeae-40ba-821b-166a75fbe8c3qthemeqauth_type'


from pages.avtn_page inport AutPage
inport time 
def test_testauth_page(web_driver):
page=AuthPage(web_driver)
#page.enter_email(value="email@gmail.com")
#page.enter_pass(value="pass")
#
# #знак != или == будет зависеть от того, верные или неверные данные мы вводим
# assert page.get_relutive_link() != "/allpe login
И метод   @allure.step("Решение капчи")
    def solve_captcha(self, captcha_image_url, page_url):
        """

from selenium.webdriver.common.by import By

class AuthLocators:
AUTH_ELAIL = (By.ID, "username")
AUTH_PHONE = (By.ID, "username")
AUTH_LOGIN = (By.ID, "username")
AUTH_ACCOUNT = (By.CLASS_NAME, "rt-input__input rt-input__input --rouder rt-input__input--orange ")
AUTH_PASS = (By.ID, "password")
AUTH_BTN = (By.ID,"kc-login")
     
def test_login_by_phone(web_driver, phone, password):
    page = AuthPage(web_driver)
    page.open_auth_page()
    # Ввод номера телефона
    page.enter_phone(phone)
    # Ввод пароля
    page.enter_pass(password)
    # Нажатие кнопки "Войти"
    page.btn_click()
    # Находим элемент изображения капчи
    captcha_image_element = web_driver.find_element(AuthLocators.AUTH_CAPTCHA_IMG)
    # Получаем значение атрибута src изображения капчи
    captcha_image_url = captcha_image_element.get_attribute('src')
    # Ожидаем, пока изображение капчи загрузится
    WebDriverWait(web_driver, 10).until(EC.presence_of_element_located(AuthLocators.AUTH_CAPTCHA_IMG))
    # Если изображение капчи отображается и доступно для взаимодействия, вызываем функцию для ее решения
    if captcha_image_element.is_displayed() and captcha_image_element.is_enabled():
        page_url = web_driver.current_url  # URL текущей страницы
        captcha_text = page.solve_captcha(captcha_image_url, page_url)
И метод   @allure.step("Решение капчи")
    def solve_captcha(self, captcha_image_url, page_url):
        """
        Решает капчу с помощью сервиса 2captcha.
        :param captcha_image_url: Ссылка на изображение капчи.
        :param page_url: URL текущей страницы.
        :return: Текст, введенный в капчу.
        """
        api_key = "bda49f557a8791280e7b07845df733d4"  

class AuthrizationFormTest(unittest.TastCase):
  def setUp(self):
    self.driver = webdriver.Chrome()
    selt.driver.get("https:b2c.passport.rt.ru/")

 deftest_display_authorization_form(self):
   autforization_form = WEbDriver Wait(self.driver, 10).until(Ec.presence_of_element_located((By.ID, "page-right"))
)
self.assertTrue(authorization_form.is_displayed())

def test_registration_success(self):
  self.navigate_to_registration()
  self.fill_registretion_form(first_name=os.qetenv("validfirst")

        # Отправляем запрос на распознавание капчи
        captcha_url = f"http://2captcha.com/in.php?key={api_key}&method=base64&body={captcha_image_url}&pageurl={page_url}"
        response = requests.get(captcha_url)
        captcha_id = response.json().get("request")
        if not captcha_id:
            raise Exception("Не удалось получить ID капчи")

        # Ожидаем, пока капча будет распознана
        time.sleep(10)

        # Получаем результат распознавания капчи
        captcha_url = f"http://2captcha.com/res.php?key={api_key}&action=get&id={captcha_id}"
        response = requests.get(captcha_url)
        captcha_text = response.json().get("request")
        if not captcha_text:
            raise Exception("Не удалось распознать капчу")

        return captcha_text



        # Находим элемент поля ввода капчи
        captcha_input_element = web_driver.find_element(AuthLocators.AUTH_CAPTCHA_INPUT)

        # Вводим текст капчи в поле ввода
        captcha_input_element.send_keys(captcha_text)

        # Нажимаем кнопку "Подтвердить"
        captcha_input_element.submit()

    # Ожидание пока произойдет авторизация
    WebDriverWait(web_driver, 10).until(EC.visibility_of_element_located((By.CSS_SELECTOR, '.user-name')))

    # Проверка что авторизация прошла успешно
    assert web_driver.find_element(*AuthLocators.AUTH_USER_NAME).text == 'Коздринь\nРоман Романович'


def test_login_by_phone(web_driver, phone, password):
    page = AuthPage(web_driver)
    page.open_auth_page()
    # Ввод номера телефона
    page.enter_phone(phone)
    # Ввод пароля
    page.enter_pass(password)

    # Нажатие кнопки "Войти"
    page.btn_click()

    # Находим элемент изображения капчи
    captcha_image_element = web_driver.find_element(AuthLocators.AUTH_CAPTCHA_IMG)

    # Если изображение капчи отображается и доступно для взаимодействия, вызываем функцию для ее решения
    if captcha_image_element.is_displayed() and captcha_image_element.is_enabled():

        time.sleep(10)

        # Находим элемент изображения капчи снова, так как после обновления страницы элемент может стать неактуальным
        captcha_image_element = web_driver.find_element(AuthLocators.AUTH_CAPTCHA_IMG)

        captcha_image_url = captcha_image_element.get_attribute('src')
        page_url = web_driver.current_url  # URL текущей страницы
        captcha_text = page.solve_captcha(captcha_image_url, page_url)

        # Находим элемент поля ввода капчи
        captcha_input_element = web_driver.find_element(AuthLocators.AUTH_CAPTCHA_INPUT)

        # Вводим текст капчи в поле ввода
        captcha_input_element.send_keys(captcha_text)

        time.sleep(3)

        # Нажимаем кнопку "Подтвердить"
        captcha_input_element.submit()
        time.sleep(3)
        page.enter_phone(phone)
        time.sleep(3)
        # Ввод пароля
        page.enter_pass(password)
        time.sleep(3)

        # Нажатие кнопки "Войти"
        page.btn_click()
        cookies= [{'domain': '.start.rt.ru', 'expiry': 1713008814, 'httpOnly':
# Проверка что авторизация прошла успешно
    assert web_driver.find_element(AuthLocators.AUTH_USER_NAME).text == 'Коздринь\nРоман Романович'


from selenium.webdriver.common.by import By

class AuthLocators:
   AUTH_EMAIL = (By.ID, "username")
   AUTH_PHONE = (By.ID, "username")
   AUTH_LOGIN = (By.ID, "username")
   AUTH_ACCOUNT = (By.CLASS_NAME, "rt-input__input")
   AUTH_PASS = (By.ID, "password")
   AUTH_BTN = (By.ID, "kc-login")
   AUTH_BTN_EMAIL = (By.ID, "t-btn-tab-mail")
   AUTH_BTN_LOGIN = (By.ID, "t-btn-tab-login")
   AUTH_BTN_ACC = (By.ID, "t-btn-tab-ls")
   AUTH_BTN_VK = (By.ID, "oidc_vk")
   AUTH_BTN_OK = (By.ID, "oidc_ok")

from pages.auth_page import AuthPage
import time


def test_auth_page_ok(selenium):
   page = AuthPage(selenium)
   page.btn_ok_click()
   page.enter_email_ok("yandex@yandex.ru")


   time.sleep(5)
   if selenium.current_url == 'https://connect.ok.ru/dk?st.cmd=OAuth2Login&st.redirect=%252Fdk%253Fst.cmd%253DOAuth2Permissions%2526amp%253Bst.scope%253Dlogin%25253Aemail%2526amp%253Bst.response_type%253Dcode%2526amp%253Bst.show_permissions%253Doff%2526amp%253Bst.redirect_uri%253Dhttps%25253A%25252F%25252Fb2c.passport.rt.ru%25252Fsocial%25252Fadapter%25252Fok%25252Fauth%2526amp%253Bst.state%253D18hs_sBO8HvuI4Xah1VNo_ahXGCkCrmOTn0JSH4p6iU.SYnU9AJf5zo.lk_decosystems%2526amp%253Bst.client_id%253D1272957184&st.client_id=1272957184':
      
      

