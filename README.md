# scrollToTop.jsx

### import React, { useEffect, useState } from "react";
### import { FaArrowUp } from "react-icons/fa";

### const ScrollTop = () => {
###  const [isVisible, setIsVisible] = useState(false);

###  const goToBtn = () => {
###    window.scrollTo({ top: 0, left: 0, behavior: "smooth" });
###  };

###  const listenToScroll = () => {
###    let heightToHidden = 20;
###    const winScroll =
###      document.body.scrollTop || document.documentElement.scrollTop;

###    if (winScroll > heightToHidden) {
###      setIsVisible(true);
###    } else {
###      setIsVisible(false);
###    }
###  };

###  useEffect(() => {
###    window.addEventListener("scroll", listenToScroll);
###    return () => window.removeEventListener("scroll", listenToScroll);
###  }, []);

###  return (
###    <>
###      <div className="flex justify-center items-center relative ">
###        {isVisible && (
###          <div className="top-btn w-9 h-9 text-2xl fixed bottom-32 md:bottom-44 z-50 right-10 flex justify-center items-center cursor-pointer text-[#fff] rounded-full bg-green-700" onClick={goToBtn}>
###            <FaArrowUp className="top-btn--icon animate-pulse" />
###          </div>
###        )}
###      </div>
###    </>
###  );
### };

### export default ScrollTop;


### _app.js

### import FooterPage from "@/components/frontPage/FooterPage";
### import HeaderPage from "@/components/frontPage/HeaderPage";
### import ScrollTop from "@/components/frontPage/ScrollTop";
### import "@/styles/globals.css";
### import { AppProgressBar as ProgressBar } from 'next-nprogress-bar';
### import Navhedar from "@/components/frontPage/Navhedar";

### export default function App({ Component, pageProps }) {


###  return (
###    <>
###      <HeaderPage />
###      <Navhedar />
###      <Component {...pageProps} />
###      <ProgressBar
###        height="4px"
###        color="#008000"
###        options={{ showSpinner: false }}
###        shallowRouting
###      />
###      <ScrollTop />
###      <FooterPage />
###    </>
###  );
### }
