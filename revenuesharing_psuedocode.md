

pragma solidity 0.9.0;

contract RevenueSharing {

using SafeMath for uint256;

struct applicant {
    uint32 totalApplicants;
    uint32 applicantShare;
}

struct jobEvent {
    uint32 eventID;
    uint32 eventShare;
}

struct recorem {
    uint32 recoremShare;
}

event webEvent_start
event webEvent_end

function getRevenue(eventID) return totalrevenue{

}

function applicantRevenue(){
    _totalRevenue = totalRevenue;
    applicantShare = 35 * _totalRevenue / 100;

}

function eventRevenue(uint _totalRevenue){
    _totalRevenue = totalRevenue;
    eventShare = 35 * _totalRevenue / 100;
}

function recoremShare(uint _totalRevenue){
    _totalRevenue = totalRevenue;
    recoremShare = 35 * _totalRevenue / 100;
}


}
