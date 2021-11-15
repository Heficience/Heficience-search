<template>
<div class="logo-large">
 <svg  height="50" viewBox="0 0 173 192" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M26.526 105.018L45.1659 143.236C58.2425 170.047 92.0401 180.419 120.73 166.427C149.419 152.434 162.053 119.415 148.977 92.6039L120.3 33.8078C118.321 29.7508 113.192 28.1767 108.851 30.294C104.51 32.4113 102.592 37.4223 104.571 41.4793L122.494 78.2268L116.202 81.2954L89.6764 26.909C87.6977 22.8521 82.5685 21.2779 78.2273 23.3953C73.8861 25.5126 71.9688 30.5236 73.9475 34.5805L97.6058 83.0873L91.3142 86.1559L63.3544 28.8297C61.3757 24.7728 56.2465 23.1986 51.9053 25.3159C47.5642 27.4333 45.6468 32.4443 47.6255 36.5012L75.5854 93.8274L69.2938 96.896L47.0693 51.329C45.0906 47.2721 39.9614 45.6979 35.6203 47.8152C31.2791 49.9326 29.3617 54.9436 31.3404 59.0005L62.254 122.383C75.3652 117.807 89.809 122.99 95.6591 134.985L89.3675 138.053C84.6359 128.352 72.2709 124.557 61.8898 129.62L58.7441 131.155L42.2549 97.3468C40.2762 93.2898 35.147 91.7157 30.8059 93.833C26.4647 95.9503 24.5473 100.961 26.526 105.018Z" fill="url(#paint0_linear_5:4)"/>
<circle cx="94" cy="112" r="45" fill="#124320"/>
<path d="M84.2189 108.232C89.2109 109.064 93.7869 109.48 97.9469 109.48C102.107 109.48 104.763 109.448 105.915 109.384C105.787 104.52 105.723 99.848 105.723 95.368C105.723 90.888 105.723 87.848 105.723 86.248C105.723 84.648 105.787 83.656 105.915 83.272C106.043 82.824 106.459 82.408 107.163 82.024C107.867 81.64 108.891 81.448 110.235 81.448C112.155 81.448 113.115 82.6 113.115 84.904V118.888C113.115 125.928 112.955 133.672 112.635 142.12C112.571 143.976 111.003 144.904 107.931 144.904C106.395 144.904 105.627 143.976 105.627 142.12L106.011 116.68C103.963 116.808 101.147 116.872 97.5629 116.872C94.0429 116.872 89.5949 116.488 84.2189 115.72C84.2189 124.168 84.6029 133 85.3709 142.216C85.4349 143.24 84.9869 144.04 84.0269 144.616C83.0669 145.128 81.8509 145.384 80.3789 145.384C78.9709 145.384 78.2029 144.648 78.0749 143.176C77.2429 134.088 76.8269 125.128 76.8269 116.296L77.4029 86.344C77.4029 85.064 77.8829 84.136 78.8429 83.56C79.8029 82.92 80.8269 82.6 81.9149 82.6C83.7069 82.6 84.6029 83.464 84.6029 85.192L84.2189 108.232Z" fill="url(#paint1_diamond_5:4)"/>
<defs>
<linearGradient id="paint0_linear_5:4" x1="51.9053" y1="25.3159" x2="120.73" y2="166.427" gradientUnits="userSpaceOnUse">
<stop stop-color="#26BD00"/>
<stop offset="1" stop-color="#29DBD0" stop-opacity="0.64"/>
</linearGradient>
<radialGradient id="paint1_diamond_5:4" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(94 110) rotate(90) scale(45)">
<stop stop-color="#00FFE0"/>
<stop offset="1" stop-color="#56935C" stop-opacity="0.67"/>
</radialGradient>
</defs>
</svg>

<span class="sub">Search</span>


</div>
</template>

<style>

.logo-large{
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
    font-weight: bold;
    letter-spacing: 0.1rem;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
    position: relative;
    z-index: 1;

}
.sub {
    margin-left: 0.5rem;
    text-align: center;
  font-family: 'Roboto', sans-serif;  
  font-size: 1.5rem;
  background: linear-gradient(to right, #00FFE0 20%, #26BD00 40%, #26BD00 60%, #00FFE0 80%);
    background-size: 200% auto;
  color: #000;
  background-clip: text;
  text-fill-color: transparent;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  -webkit-animation: shine 2s linear infinite;
          animation: shine 2s linear infinite;
  
          
}
@-webkit-keyframes shine {
  to {
    background-position: 200% center;
  }
}
@keyframes shine {
  to {
    background-position: 200% center;
  }
}

</style>
