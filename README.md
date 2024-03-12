# 33.1
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

    # Ожидание пока произойдет авторизация
    WebDriverWait(web_driver, 10).until(EC.visibility_of_element_located(AuthLocators.AUTH_USER_NAME))

    # Проверка что авторизация прошла успешно
    assert web_driver.find_element(AuthLocators.AUTH_USER_NAME).text == 'Коздринь\nРоман Романович'

